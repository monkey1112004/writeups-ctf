🗓 Ngày làm: 08/04/2025

Mục tiêu:
Giải mã chuỗi mật khẩu đã bị obfuscate (làm rối) trong mã JavaScript.
Quá trình làm:
Ban đầu, tớ mở challenge thì thấy hiện ra một khung yêu cầu nhập mật khẩu, tớ hơi rối, không biết phải làm gì tiếp...

Tớ chọn "Cancel", sau đó nhớ lại mindset mình đã định sẵn:

“Đừng tin vào những gì hiển thị, hãy xem kỹ mã nguồn!”

Vậy là tớ bấm Ctrl + U để xem source HTML của trang. Và đúng như mong đợi, tớ phát hiện một đoạn JavaScript có dạng:

   var password = unescape('%63%70%61%73%62%69%65%6e%64%75%72%70%61%73%73%77%6f%72%64');
   if (prompt("Enter password:") == password) alert("Success!");
   else alert("Wrong password!");

Tớ nhận ra:

   🔸 Biến password được gán bằng unescape(...) – đây là hàm dùng để giải mã chuỗi escape, thường dùng để làm rối mật khẩu. %63 (hex) chuyển sang chuỗi là "c" tượng tự như thế với các ký tự tiếp theo

   🔸 Nếu nhập đúng mật khẩu thì sẽ alert ra "Success!"

Tớ thử copy đoạn unescape('%63...') vào tab Console (F12) rồi Enter → và nó trả về chuỗi gốc là:
![console giải mã](https://github.com/monkey1112004/writeups-ctf/raw/main/root-me/Web-client/images/Javascript_Obfuscation_1.png)


