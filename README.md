<div align="center">
📖 Github
&emsp;&emsp; | &emsp;&emsp;
<a href="https://interview.huihut.com">📚 Docsify</a>
</div> 
<br>

<div align="center">
<a href="https://github.com/huihut/interview/">简体中文</a>
&emsp;&emsp; | &emsp;&emsp;
Tiếng Anh
</div> 
<br>
    
<b><details><summary>💡 BẬT</summary></b>	


📚 Kho lưu trữ này là tóm tắt kiến thức cơ bản cho người tìm việc và người mới bắt đầu trong lĩnh vực công nghệ C / C ++, bao gồm ngôn ngữ, thư viện chương trình, cấu trúc dữ liệu, thuật toán, hệ thống, mạng, thư viện tải liên kết và các kiến thức khác cùng với kinh nghiệm phỏng vấn, tuyển dụng, đẩy nội bộ, v.v. thông tin.

💡 Các phương pháp hỗ trợ thư mục bên: [📚 Docsify Doc](https://interview.huihut.com), [Github + TOC navigation](https://github.com/jawil/GayHub)（[TOC preview.png](https://raw.githubusercontent.com/huihut/interview/master/images/TOC预览.png)）

📄 Lưu dưới dạng PDF: Sử dụng trình duyệt Chrome để mở trang <a href="https://interview.huihut.com"> 📚 Docsify document </a>, thu nhỏ thư mục bên trái-click chuột phải-chọn in-chọn máy in mục tiêu là Lưu dưới dạng PDF-Lưu ([Print Preview.png](https://raw.githubusercontent.com/huihut/interview/master/images/PrintPreview.png))

🙏 Nếu có bất kỳ lỗi hoặc cải tiến nào trong nội dung của kho, chúng tôi hoan nghênh issues hoặc pr. Đề xuất hoặc thảo luận có thể được gửi tại [# 12](https://github.com/huihut/interview/issues/12). Do trình độ hạn chế của tôi, các điểm kiến thức trong kho đến từ bản gốc của tôi, ghi chú đọc, sách, bài đăng blog, v.v. Non-original đã được đánh dấu với nguồn, nếu có bất kỳ bỏ sót nào, vui lòng phát hành một vấn đề. Kho này tuân theo thỏa thuận [CC BY-NC-SA 4.0](https://github.com/huihut/interview/blob/master/LICENSE), vui lòng chỉ định nguồn cho việc in lại, và không được sử dụng cho mục đích thương mại.

</details>

## 📑 Mục lục

* [➕ C/C++](#cc)
* [⭐️ Hiệu quả](#effective)
* [📦 STL](#stl)
* [〽️ Cấu trúc dữ liệu](#data-structure)
* [⚡️ Thuật toán](#algorithm)
* [❓ Vấn đề](#problems)
* [💻 Hệ điều hành](#os)
* [☁️ Mạng máy tính](#computer-network)
* [🌩 Lập trình mạng](#network-programming)
* [💾 Cơ sở dữ liệu](#database)
* [📏 Mẫu thiết kế](#design-pattern)
* [⚙️ Thư viện tải liên kết](#link-loading-library)
* [📚 Sách](#books)
* [🔱 Hướng phát triển C/C++](#cc-development-direction)
* [💯 Đánh giá trang web câu hỏi](#review-of-brush-questions-website)
* [📝 Kinh nghiệm câu hỏi phỏng vấn](#interview-questions-experience)
* [📆 Bài đăng thời gian tuyển dụng](#recruitment-time-post)
* [👍 Đề xuất](#recommend)
* [👬 Người đóng góp](#contributor)
* [📜 Giấy phép](#license)

<a id="cc"></a>

## ➕ C/C++

### const

#### Chức năng

1. Chỉnh sửa biến, cho biết biến không thể thay đổi;
2. Chỉnh sửa con trỏ, chia thành con trỏ đến const (con trỏ đến const) và con trỏ là hằng số (con trỏ const, con trỏ const);
3. Chỉnh sửa tham chiếu, tham chiếu đến hằng số (tham chiếu đến const), được sử dụng cho các loại tham số chính thức, tránh việc sao chép và sửa đổi giá trị của hàm;
4. Trang trí một hàm thành viên, cho biết không thể sửa đổi biến thành viên trong hàm thành viên.

#### Con trỏ và tham chiếu const

* Con trỏ
     * Con trỏ đến const
     * Con trỏ đến một hằng số (con trỏ const)
* Tham chiếu
     * Tham chiếu đến const
     * Không có tham chiếu const vì tham chiếu là bí danh của một đối tượng, tham chiếu không phải là một đối tượng

> (Hãy nghĩ về nó cho sự tiện lợi) Giá trị được sửa đổi bởi const (sau const) không thể thay đổi, chẳng hạn như `p2`, `p3` trong ví dụ sử dụng dưới đây


#### Sử dụng

Sử dụng const

```cpp
// class
class A
{
private:
    const int a;                // thành viên đối tượng hằng số, có thể sử dụng danh sách khởi tạo hoặc khởi tạo trong lớp

public:
    // Constructor
    A() : a(0) { };
    A(int x) : a(x) { };        //  danh sách khởi tạo

    //  const có thể được sử dụng để phân biệt giữa các hàm nạp chồng
    int getValue();             //  hàm thành viên thông thường
    int getValue() const;       // hàm thành viên hằng số, không được sửa đổi giá trị của bất kỳ thành viên dữ liệu nào trong lớp
};

void function()
{
    // object
    A b;                        // đối tượng thông thường, có thể gọi tất cả các hàm thành viên
    const A a;                  // đối tượng hằng số, chỉ có thể gọi các hàm thành viên hằng số
    const A *p = &a;            // biến con trỏ, trỏ đến một đối tượng hằng số
    const A &q = a;             // tham chiếu đến đối tượng hằng số

    // pointer
    char greeting[] = "Hello";
    char* p1 = greeting;                // biến con trỏ, trỏ đến một mảng ký tự biến
    const char* p2 = greeting;          // biến con trỏ, trỏ đến một mảng ký tự hằng số (char theo sau const, chỉ ra rằng ký tự được trỏ đến (char) không thể thay đổi)
    char* const p3 = greeting;          // chính nó là một con trỏ hằng số đến một mảng ký tự biến (const theo sau p3, chỉ ra rằng con trỏ p3 không thể thay đổi)
    const char* const p4 = greeting;    // một con trỏ đến một hằng số, trỏ đến một mảng ký tự hằng số
}

// function
void function1(const int Var);           // các tham số được truyền là không thể thay đổi trong hàm
void function2(const char* Var);         // Nội dung được trỏ đến bởi con trỏ tham số là hằng số
void function3(char* const Var);         // con trỏ tham số là hằng số
void function4(const int& Var);          // tham chiếu tham số là hằng số bên trong hàm

// giá trị trả về của hàm
const int function5();      // trả về một hằng số
const int* function6();     // trả về một biến con trỏ đến một hằng số, sử dụng: const int * p = function6 ();
int* const function7();     // trả về một con trỏ hằng số đến một biến, sử dụng: int * const p = function7 ();
```

