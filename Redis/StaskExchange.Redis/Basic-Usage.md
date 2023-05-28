# Basic Usage

## Tài liệu tham khảo

[Basic usage](
https://stackexchange.github.io/StackExchange.Redis/Basics)

## ConnectionMultiplexer

Đối tượng trung tâm của `StackExchange.Redis` là class `ConnectionMultiplexer`, đối tượng dùng để kết nối đến **multiple server** để **share and reused** giữa các lần call.
Sử dụng `ConnectionMultiplexer.Connect` hoăc `ConnectionMultiplexer.ConnectAsync`, passing các cấu hình `configuration string` hoặc `ConfigurationOptions` để khởi tạo một kết nối.

    using StaskExchange.Redis;
    ...
    ConnectionMultiplexer redis = ConnectionMultiplexer.Connect("localhost:6379"); // Đồng bộ
    ConnectionMultiplexer redis = ConnectionMultiplexer.ConnectAsync("localhost:6379"); // Bất đồng bộ
    ConnectionMultiplexer redis = ConnectionMultiplexer.ConnectAsync("server1:6379,server2:6379"); // Nhiều server primary/replica

`ConnectionMultiplexer` có 3 thứ chính:

- Truy cập vào redis database
- Sử dụng tính năng pub/sub của redis
- Truy cập vào server với mục đích maintenance hoặc monitoring.

### Using a redis database

Truy cập vào redis database:

    IDatabase db = redis.GetDatabase();

Lệnh trên trả về danh sách db. Lưu ý redis hỗ trợ **multiple databases (16)**, có thể lấy chính xác db từ `GetDatabase` bằng cách thêm `Task.AsyncState`.

    int databaseNumber = ...
    object asyncState = ...
    IDatabase db = redis.GetDatabase(databaseNumber, asyncState);

Sau khi đã có `IDatabase`, nó có thể sử dụng các **redis API** đơn giản

    string key = ..., value = ... // string
    byte[] key = ..., value = ... // raw binary
    db.StringSet(key, value);
    db.StringSetAsync(key, value);
    ...
    string value = db.StringGet(key);
    string value = db.StringGetAsync(key);


### Using redis pub/sub

Bất cứ cộng đồng sử dụng redis đều có distribution tool **pub/sub message**

#### Publish

    sub.Publish("messages", "hello");

#### Subscriber

    ISubscriber sub = redis.GetSubcriber();

Lưu ý tất cả subscription là **global** chúng không phải là scoped lifetime of `ISubscriber` instance. Tính năng **pub/sub** trong redis sử dụng tên là **channels**. Trong cộng đồng .NET subsriptions là một *callback delegates* với *channels name và message*

    sub.Subscribe("messages",(channel, message) => {
        // TODO
        ...
    })

Trong *v2*, subscriber ngoài cung cấp một *callback delegates* trực tiếp từ `Subscriber` method, bạn có thể sử dụng `ChannelMessageQueue` thay thế và **ordered pub/sub** thông báo.

    sub.Subsribe("messages").OnMessage(channelMessage => {
        // TODO
        ...
    });

    sub.Subsribe("messages").OnMessage(async channelMessage => {
        // TODO
        await Task.Delay(1000);
        ...
    });

### Accessing individual servers

Dành cho mục đích maintenance, bạn có thể truy cập vào server với lệnh:

    IServer server = redis.GetServer("localhost", 6379);

Bạn có thể truy cập các `Endpoint` như sau:

    Endpoint [] endpoinds = redis.GetEndPoints();