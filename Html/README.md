# HTML Tutorial

## HTML?

### [Tài liệu tham khảo](https://www.w3schools.com/tags/default.asp)

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