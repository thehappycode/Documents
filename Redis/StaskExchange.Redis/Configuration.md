# Configuration

## Tài liệu tham khảo

[Configuration](https://stackexchange.github.io/StackExchange.Redis/Configuration)

`Configuration` có hai cách:

- `string` representing the configuration
- `ConfigurationOptions` install

## Basic Configuration Strings

Đơn giản với cấu hình *server:port* và *options* như sau:

    var conn = ConnectionMultiplexer.Connect("redis0:6379,redis1:6380,allowAdmin=true");

Nếu bạn sử dụng một `serviceName` trong **connection string**, nó sẽ **trigger sang chế độ sentinel mode**. Ví dụ chúng ta kết nối đến *sentinel server* trên máy local sử dụng *default sentinel port (26379)* với *primary server* là `myprimary`. Primary service sẽ tự động upload nếu primiray thay đổi:

    var conn = ConnectionMultiplexer.Connect("localhost,serviceName=myprimary");

Chúng ta có thể **mapping** hai chiều giữa `string` và `ConfigurationOptions` như sau:

    var options = ConfigurationOptions.Parse(configurationString);
    var configurationString = options.ToString();

Bạn có thể apply chi tiết cấu hình khi runtime:

    string configurationString = GetRedisConfiguration();
    var options = ConfigurationOptions.Parse(configurationString);
    options.ClientName = GetAppName();
    options.AllowAdmin = true;
    conn = ConnectionMultiplexer.Connect(options);

## Configuration Options

Xem chi tiết thược tính của đối tượng [ConfigurationOptions](https://stackexchange.github.io/StackExchange.Redis/Configuration#configuration-options) tại đây.


## Obsolete Configuration Options

Những cấu hình lỗi thời không được hỗ trợ như `responseTimeout={int}`, `writeBuffer={int}`

## Automatic and Manual Configuration

Trong nhiều kịch bản (scenarios), *StackExchange.Redis* sẽ tự động cấu hình rất nhiều *settings*, bao gồm:

- Server type and version.
- Connection timeouts.
- Primary/Replica relationships.

Đôi khi bạn muốn bỏ qua chúng, các lệnh có thể **disabled** redis server trong trường hợp này như sau:

    ConfigurationOptions config = new ConfigurationOptions
    {
        EndPoints = 
        {
            {"redis0", 6379},
            {"redis1", 6380}
        },
        CommandMap = CommandMap.Create(new HashSet<string>{
            // EXCLUDE a few commands
            "INFO", "CONFIG", "CLUSTER",
            "PING", "ECHO", "CLIENT"
        }, available: false),
        KeepAlive = 180,
        DefaultVersion = new Version(2, 8, 8),
        Password = "myPassword"
    };

ConfigurationOptions sẽ tương ứng với configurationString:

    redis0:6379,redis1:6380,keepAlive=180,version=2.8.8,$CLIENT=,$CLUSTER=,$CONFIG=,$ECHO=,$INFO=,$PING=

Một dễ dàng hơn khi không sử dụng một số tính năng của redis bằng **disable and/or rename** sử dụng `Dictionary<string,string>` thay thế cho cách sử dụng `HashSet<string>` ở ví dụ trên như sau:

    var commands = new Dictionary<string, string>{
        {"info", null}, // disabled.
        {"select", "use"} // renamed to SQL equivalent of some reason.
    }

    var options = new ConfigurationOptions {
        CommandMap = CommandMap.Create(commands);
    }

Tất cả các commands không có trong dictionary sẽ enabled và không đổi tên. Một `null` or **blank** sẽ là *disabled*
ConfigurationOptions sẽ tương ứng với configurationString:

    $INFO=,$SELECT=use

## Redis Server Permisions