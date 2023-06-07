# Keys - Values - Channels

## Tài liệu tham khảo

[Keys - Values - Channels](https://stackexchange.github.io/StackExchange.Redis/KeysValues)

## Keys

`Keys` trong **StackExchange.Redis** có kiểu là `RedisKey`. `Keys` được có 2 dạng là `string` hoặc `byte[]`. `StringIncrement` là một phương thức của `RedisKey` *return* một giá trị *random*.

    string key = ...
    db.StringIncrement(key);

    byte[] key = ...
    db.StringIncrement(key);

    string someKey = db.KeyRandom();

## Values

`Values` trong **StackExchange.Redis** có kiểu là `RedisValue`.

    db.StringSet("mykey", 123)

Lưu ý: Khi `get` `keys` không tồn tại thì `values` sẽ có giá trị là **0** tương ứng với `nil`.

    db.KeyDelete("mykey");
    int i = (int)db.StringGet("mykey"); // this is ZERO or throw exception.
    bool isNil = value.IsNull; // this is true.

## Hashes

## Channel

`Channel` trong **StackExchange.Redis** có kiểu `RedisChannel`. Nó là một `RedisKey` lớn hơn, nhưng handler độc lập với *channel-names* cho đến khi đúng với *first-class elements*. Chúng không có hiểu quả với command **routing**.

## Scripting

[Lua scripting in redis](https://redis.io/commands/EVAL) có 2 tính năng quan trọng

- Input bắt buộc tách riêng `keys` và `values`.
- Dữ liệu trả về không cần phải định nghĩa.

Phương thức `ScriptEvaluate` cho phép tách biệt *hai array input*, một `RedisKey[]`, một `RedisValue[]`

    var result = db.ScriptEvaluate(TransferScript, // TransferScript là một string chứa Lua
        new RedisKey[] {from, to}, new RedisValue[]{quantity}
    );

`result` trong ví dụ trên là một kiểu `RedisResult`. `RedisResult` offers a range of conversion operations -more, in fact than`RedisValue`, bởi nó được thêm vào việc dịch text, binary, primitives and nullable-primitives được trình bày trong một array.

    string[] items = db.ScriptEvaluate(...);
