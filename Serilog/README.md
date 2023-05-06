# [Serilog](https://serilog.net)

Serilog là thư viện của .NET cung cấp diagnostic logging to files, console, v/v...

## Serilog message templates

Ví dụ về Serilog message templates

    var position = new {Latitude = 25, Longitude = 123};
    var elapsedMs = 34;
    log.Information("Processed {@Position} in {Elaped:000} ms.", position, elapsedMs);

- `@` trước Position nói cho Serilog là serialize object.
- `:000` phía sau Elapsed là format string chuẩn của .NET với thuộc tính sau khi rendered.

Kết quả nhận được khi hiển thị message trong logging như sau:
> 09:12:22 [Information] Processed {Latitude: 25, Longitude: 123} in 034 ms.

---

# [Writting Log Events](https://github.com/serilog/serilog/wiki/Writing-Log-Events)

## Message template syntax

Message template có syntax giống hệt với syntax chuẩn của .NET `string.Formate()`.

    Log.Warning()"Disk quota {Quota} exceeded by {User}", quota, user);

## Message template recommendations

    // Dont'
    Log.Information("The time is " + DateTime.Now);

    // Do
    Log.Information("The time is {Now}", DateTime.Now);
Property Naming - Sử dụng kiểu **PascalCase**
Bạn có thể  tham khỏa về message template syntax tại [messagetemplates.org](https://messagetemplates.org)

## Log event levels

STT | Tên levels  | Diễn giải
----|-------------|----------
1   | Verbose     | Tracing information và debugging.
2   | Debug       |  
3   | Information |
4   | Warning     |
5   | Error       |
6   | Fatal       | Critical error (Lỗi nghiêm trọng) causing (nguyên nhân) complete failure of application.

## Dynamic levels

Nhiều app lớn/phân tán cần hạn chế các level của logging. Mặc định current minimum level là `Infomation`.

## Source Contexts

## Correlation

`ForContext<T>()` tag log events ghi với class, other overloads `ForContext` cho phép log events có thể tagged với *identifier* hỗ trợ *correlation*.

    var job = GetNextJob();
    var jobLog = Log.ForContext("JobId", job.Id);
    jobLog.Information("Running a new job");
    job.Run();
    jobLog.Information("Finished");

Đoạn code trên cả 2 log event sẽ mang theo ***JobI***.

---

# [Configuration Basic](https://github.com/serilog/serilog/wiki/Configuration-Basics)
