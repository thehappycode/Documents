# Everyday Types

## The primitives: `string`, `number`, `boolean`

## Arrays

## any

Typescript có một kiểu dữ liệu **đặc biệt** là `any`, bạn có thể dùng bất kỳ nới nào mà không cần **check lỗi**. Nếu khai báo kiểu `any` thì *object* sẽ giống như *pure javascirpt*.

## noImplicitAny

Khi không biết chính xác một kiểu dữ liệu, và **Typescript** sẽ compiler về kiểu mặc định là `any`. Bời vì kiểu `any` không **type-check**, để khắc phục việc này ta sẽ gán *flag* `noImplicitAny`để bấy kỳ kiểu dữ liệu `any` sẽ bị lỗi.

## Type Annotations on Variables

Khi bạn khai báo các biến sử dụng `keywork` là: `var`, `let`, `const` thì bạn cần thêm một **anotation** của kiểu dữ liệu

    var nyUserName: string = "tamnt4"

Trong hầu hết các trương hợp **Typescript** có thể tự động suy luận (infer) ra kiểu dữ liệu trong code của bạn.

## Function

**Typescript** cho phép bạn định nghĩa chính xác cả 2 kiểu dữ liệu của *input* và *output* trong một function.

### Parameter Type Anotations

Khi bạn khai báo một *function*, bạn có thể thêm các kiểu *type anotations* sau mỗi *parameter*.

    function greet(name: string){
        console.log(`Helllo, ${name}!`)
    }

## Return Type Anotations

Bạn có thể thêm một `return` type anotaions sau danh sách parameters

    function greet(): string {
        console.log("Hello world!")
    }

Giống như variable type **anotations**, bạn cũng không cần phải định nghĩa `return` type anotations bời vì **Typescript** sẽ tự suy luận ra từ kiểu dữ liệu tra của câu lệnh `return`.

### Anonymous Function

**Anonymous function** có một ít khác biệt với **function declare**. Bổi vì **Typescript** sẽ tự động xắc định kiểu dữ liệu của parameters hoặc kết quả trả về từ `return` khi call function.

    const names = ["tamnt4", "trangttt1"]
    names.forEach(function(name){
        console.log(name.toUpperCase())
    })

## Object Types

### Options Properties

**Object** có thể, có một vài hoặc tất cả các **properties** là *optional*. Thử nhá, thêm `?` sau *property* name. Trong **Javascript**, nếu bạn truy cập một *property* không tồn tại, bạn sẽ nhận được giá trị là `undefined` đúng hơn là runtime error. Bởi vì lý do này, khi bạn đọc một *optional property* bạn có thể check `undefined` trước khi sử dụng.

## Union Types

**Typescript** cho phép bạn build một **new type** từ nhiều kiểu dữ đã tồn tại trước đó.

### Defining a Union Type

*Union type* là tập hợp từ *hai* hoăc *nhiều* kiểu dữ liệu khác nhau.

    function printId(id: number | string){
        console.log(`Your Id is: ${id}`)
    }

### Working with Union Types

**Typescript** chỉ cho phép các hành động nếu valid hết tất cả các thành phần của union. Như ví dụ sau sẽ gây lỗi:

    function printId(id: number | string){
        console.log(id.toUpperCase()) // Error do không valid được type number.
    }

Để giải quyết lỗi trên chúng ta có thể dùng (**narrow the union**) so sánh kiểu dữ liệu cơ bản

    function printId(id: number | string | []string boolean){
        if(typeof id === "string"){
            console.log(id.toUpperCase())
        }
        else if{
            consolog.log(id)
        }
        else {
            if(Array.isArray(number)){
                    console.log(x.join(" and "))
                }
        }
    }

## Type Aliases

Chúng ta sử dụng **object types** và **union types** để ghi các anotations lên chúng. Tiện lợi hơn, nếu bạn muốn sử dụng kiểu dữ liệu đó nhiều lần hơn và nó có thể refer (tự suy) ra được từ một single name. Bạn có thể sử dụng **type alias**.

    type Point = {
        x: number;
        y: number;
    }

    function printCoord(point: Point){
        console.log(`x: ${point.x} - y: ${point.y}`)
    }

    printCoord({x: 10, y: 20})


## Interfaces

Một `interface` là một cách khai báo khác của **object type**

    interface Point {
        x: number;
        y: number;
    }

    function printCoord(point: Point){
        console.log(`x: ${point.x} - y: ${point.y}`)
    }

    printCoord({x: 10, y: 20})

**Interfaces** và **Type Aliases** phía trên giống hệ nhau, làm thể nào để phân biệt được 2 loại này

### [Differences Between Type Alias and Interface](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces)

**Type Aliases** và **Interfaces** rất giống nhau, và trong nhiều trường hợp bạn có thể chọn tự do chọn lựa. Hầu hết các feature của một `interface` đều có trong `type`, nhưng có một số khác biệt nhỏ về `keyword` để mở rộng (extension) và `interface` có thể thêm mới một *new field* còn `type` thì *không* được thay đổi kiểu dữ liệu được tạo trước đó.

## Type Assertions (Xác nhận)

**Typescript** sẽ convert chính xác kiểu dữ liệu

    const a = (expr as any) as T

## Literal Types

    const alignment = "left" | "center" | "right"

## `null` and `undefined`

### `strictNullChecks` off

Với `strictNullChecks` off, giá trị `null` hoăc `undefined` có thể truy cập và gán cho các property một cách bình thường, giống như các ngôn ngữ khong kiểm tra `null`, các bug về `null` và `undefined` rất khó kiểm tra, nên recommend mọi người bật `strictNullCheck` on.

### `strictNullCheck` on 

Với `strictNullChecks` on, bạn cần phải kiểm tra giá trị là `null` hoặc `undefined` trước khi sử dụng chúng.

    function doSomething(x: string | null){
        if(x === null){
            // TODO ...
        }
        else
        {
            // TODO ...
        }
    }

### Non-null Asertion Operator (Postfix !)

**Typescript** có một syntax đặc biệt để remove `null` và `undefined` mà không cần kiểm tra chúng. Bạn có thể thêm `!` vào sau bất kỳ một biểu thức (expression) nào nếu biết chắc nó khác `null` hoặc `underfined`

    function liveDangerously(x?: number | null | undefined){
        console.log(x!.toFixed()) // No error.
    }

## [Enums](https://www.typescriptlang.org/docs/handbook/enums.html)

## Less Common Primitives

### `bigint`

Từ `ES2020` **Javascript** sử dụng kiểu dữ liệu large integers là `BigInt`:

    // Creating a bigint via BigInt function
    const onHundred: bigint = BigInt(100);

    // Creating a bigint via the literal syntax
    const onHundred: bigint = 100n

### `symbol`

`symbol` là một kiểu dữ liệu cơ bản của **Javascript**, nó tạo một **global unique** thông qua function `Symbol()`

    const firstName = Symbol("name);
    const secondName = Symbol("name);

    if(firstName === secondName) // Error
    {
        // TODO ...
    }