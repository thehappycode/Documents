# HTML Tutorial

## [Tài liệu tham khảo](https://www.w3schools.com/tags/default.asp)

## HTML là gì?

HTML là một cụm từ được viết tắt *Hyper Text Markup Language* dịch ra là **Ngôn ngữ đánh dấu siêu văn bản** (nghe ngu vãi).
HTML được dùng để tạo ra một trang Web.
Một trang HTML được kết hợp từ nhiều phần tử thẻ (element tag). Mỗi thẻ sẽ nối cho browser biết cách hiển thị nội dung khác nhau.
Để có thể hiểu rõ hơn thì ta có thể xem một trang web với một trang word chỉ khác là website có thêm phần URL? Vậy URL là gì? URL đại điện cho một địa chỉ server? Nếu thích thú thì bạn nên like và share hoặc comment chủ để URL để tôi làm một bài chi tiết về nó :)

## Lịch sử HTML.

HTML được một thanh niên tên người Anh tên là Tim Berners-Lee phát minh năm 1989.
Trải qua bao nhiêu năm tháng thăng trầm biến động của lịch sử thì đến năm 2017 phiên bản cuối cùng là HTML5.2.

## HTML hoạt động như thê nào?

Thật sự thiếu sót nếu không nói về cách thức hoạt động của một trang Web.
Website hoạt động bằng một giao thức (Prototol) gọi là (HTTP) giữa máy khách và máy chủ.
Vậy giao thức (Protocal) là gì? Là một bộ các quy tắc cho phép các máy tính trao đổi thông tin với nhau nó tương tụ như ngôn ngữ để 2 người nói chuyện đc với nhau. Trong trường hợp HTTP là giao thức cho phép máy khách (client) và máy chủ (server). Éo hiểu mấy ông thời xưa dịch chữ server thành chủ đươc? :(((

## Cấu trúc một trang HTML

    <!DOCTYPE html>
        <html>
            <head>
                <title>Page Title</title>
            </head>
            <body>
                // Content
                <h1>This is a heading <h1>
                <p>This is a paragraph.</p>
            </body>
        </html>

## Syntax

    Như đã giới thiệu ở phần trên một trang HTML là sự kết hợp của nhiều phân tử thẻ (element tag). Quy tắc bắt buộc của một tag là nếu mở thẻ thì phải đóng thẻ trừ một thẻ đặc biệt như `<!DOCTYPE html>`

    <!DOCTYPE html>
    <html>
    <body>

    <h1>My First Heading</h1>

    <p>My first paragraph.</p>

    </body>
    </html>

## Danh sách tags thông dụng

- `<!DOCTYPE>`: Định nghĩa loại tài liệu
- `<a>`: Định nghĩa một link.
- `<b>`: Định nghĩa chữ in đậm.
- `<body>`: Phần thân của tài liệu.
- `<br>`: Định nghĩa xuống dòng.
- `<button>`: Định nghĩa một nút.
- `<canvas>`: Được dùng trong vẽ hình ảnh.
- `<col>`: Định nghĩa columns trong table.
- `<div>`: Định nghĩa một mục trong tài liệu (tag dùng phổ biến nhất).
- `<em>`: Định nghĩa chữ in nghiêng.
- `<form>`: Định nghĩa một form dùng để nhập dữ liệu
- `<h1>, <h2>, <h3>, <h4>, <h5>, <h6>`: Định nghĩa các header, kích thước chữ sẽ giảm dần từ *h1* xuống *h6*
- `<header>`: Định nghĩa một header (thường chứa các liên kết ngoài).
- `<hr>`: Định nghĩa một đường kẻ.
- `<i>`: Giống như *em* định nghĩa chữ in nghiêng.
- `<img>`: Định nghĩa một hình ảnh.
- `<input>`: Định nghĩa input.
- `<label>`: Định nghĩa nhãn cho input.
- `<li>`: Định nghĩa 1 item của list
- `<link>`: Định nghĩa liên kết với tài nguyên bên ngoài như file css, thư viện...
- `<main>`: Định nghĩa phần chính tài liệu chính.
- `<nav>`: Định nghĩa một navigation link trong menu.
- `<ol>`: Định nghĩa order list.
- `<option>`: Định nghĩa 1 option trong dropdown list.
- `<p>`: Định nghĩa 1 đoạn văn.
- `<pre>`: Định nghĩa 1 đoạn văn nhưng được format text như khi nhập.
- `<script>`: Định nghĩa một script code của javascript.
- `<section>`: Định nghĩa một section
- `<select>`: Định nghĩa một dropdown list.
- `<strong>`: Giống như **b** dùng để in đậm chữ.
- `<style>`: Định nghĩa style của thẻ.
- `<span>`: Định nghĩa một section (tag được dùng phổ biến).
- `<svg>`: Định nghĩa một hình ảnh dạng svg.
- `<table>`: Định nghĩa một bảng.
- `<tbody>`: Định nghĩa nội dung của bảng.
- `<td>`: Định nghĩa một ô.
- `<textare>`: Định nghĩa vùng input.
- `<tfooter>`: Định nghĩa footer của table.
- `<th>`: Định nghĩa ô của theader.
- `<thead>`: Định nghĩa header của table.
- `<tr>`: Định nghĩa một dòng của table.
- `<u>`: Định nghĩa gạch chân của chữ.
- `<ul>`: Định nghĩa unordered list.

## Ví dụ và kết hợp các tags.

### `<h1>, <h2>, <h3>, <h4>, <h5>, <h6>`
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>

<hr />
### `<form>, <label> <input>, <textarea>, <button>, <br>`
<form>
    <label>Nhập họ: </label> 
    <input />
    <br />
    <label>Nhập tên: </label>
    <input />
    <br />
    <label>Giới tính: </label>
    <input type="checkbox"> Nam
    <input type="radio"> Nữ
    <br>
    <label>Quê quán: </label>
    <textarea></textarea>
    <br />
    <button>Submit </button>
</form>

<hr />
### `<img>`
<img src="https://thuthuatphanmem.vn/uploads/2018/09/11/hinh-anh-dep-1_044126531.jpg"/>

<hr />
### `<nav> <a>`
<nav>
    <a href="https://google.com">Google</a> |
    <a href="https://facebook.com">Facebook</a> |
    <a href="https://www.netflix.com/vn">Netflix</a> |
    <a href="https://youtube.com">Youtube</a>
</nav>

<hr />
### `<ol>, <ul>, <li>`
<ol>
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
</ol>
<ul>
    <li>item 1</li>
    <li>item 2</li>
    <li>item 3</li>
</ul>

<hr />
### `<select>, <option>`
<select>
    <option>option 1</option>
    <option>option 2</option>
    <option>option 3</option>
</select>

<hr />
### `<table>, <thead>, <tbody>, <thead>, <tfooter>, <tr>, <th>, <td>`

<table>
    <thead>
        <tr>
            <th>Month</th>
            <th>Savings</th>
        </tr>
    <thead>
    <tbody>
        <tr>
            <td>January</td>
            <td>$100</td>
        </tr>
        <tr>
            <td>February</td>
            <td>$80</td>
        </tr>
    <tfooter>
        <tr>
            <td>Sumary</td>
            <td>$180</td>
        </tr>
    </tfooter>
</table>