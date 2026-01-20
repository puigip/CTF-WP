![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image1.png){width="6.5in"
height="4.7965277777777775in"}

Ở bài này nó có gợi ý là không dung SQLinjection

![A screenshot of a login screen AI-generated content may be
incorrect.](./media/media/image2.png){width="6.5in" height="3.1875in"}

Đầu tiên ta có 1 trang đăng nhập và 1 trang đăng kí

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image3.png){width="6.5in"
height="3.504861111111111in"}

Vì đề bài nói không sử dụng sql injection nên tôi cũng không kiểm tra
quá nhiều ở chức năng đăng nhập và đăng kí , đơn giản là tạo tài khoản
và vào trang chủ của nó thôi

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image4.png){width="6.5in"
height="3.5430555555555556in"}

Vào tới trang chủ ta có 1 chức năng upload file

Ở đây website chỉ cho phép upload file ảnh

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image5.png){width="6.5in"
height="3.026388888888889in"}

Tôi đã thử upload 1 số đuôi file dạng .php, .phar , phtml , đều bị chặn

Và khi upload file lên server thành công thì ta sẽ có thấy 1 đường dẫn
trỏ tới file

Dùng burp để check thì như sau

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image6.png){width="6.5in"
height="2.5340277777777778in"}

Thấy url có nhận giá trị tham số là tên file , tôi thử tcong path
traversal

Payload

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image7.png){width="6.5in"
height="2.907638888888889in"}

\~\~ Đọc được luôn file passwd , tôi thử đọc 1 số file khác của hệ thống
như file shadow

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image8.png){width="6.5in"
height="3.203472222222222in"}

Như vậy backend server chạy với quyền khá cao ( root )

Tôi sẽ đọc them 1 số file quan trọng khác /proc/self/environ lưu các
biến môi trường của system

(Thực là là đọc hết 1 lượt file rồi mới thấy file có chứa dấu hiệu của
flag ở đây tôi cũng mất khá nhiều thời gian để mò =)) )

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image9.png){width="6.5in"
height="1.8166666666666667in"}

Ở đây có chứa đường dẫn tới flag

![A screenshot of a computer AI-generated content may be
incorrect.](./media/media/image10.png){width="6.5in"
height="1.8472222222222223in"}

Done
