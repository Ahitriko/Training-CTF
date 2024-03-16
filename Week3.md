1 Elliot_secrets
đầu tiên em dùng lệnh file và exiftool để xem thông tin từ file elliot-secrets.bin
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9f37efd9-3561-43bd-802e-1eeb8592f1b0)
sau đó em dùng lệnhn foremost elliot_secrets.bin để phục hồi dữ liệu của file này và em thấy xuất hiện thêm một file là output_Sat_Mar__9_18_14_05_2024
(tại vì em dùng lệnh này với file elliot_secrets.bin nên nó đã có file output r nên dùng lại nó sẽ xuất hiện file có tên như trên)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/0eff8832-5e24-4fe9-9628-d5c547d67447)
khi em truy cập vào directory này thì xuất hiện một diractory là wav
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ab2bb1a1-e401-42af-865b-a7083de841d4)
khi truy cập vào nó em thấy xuất hiện một file là 000000039.wav
em có tìm hiểu được đây là một file âm thanh
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c6d27678-fb9d-4fd1-9456-699019ad9969)
(wav là file wave audio)
em có biết được là dạng fike này mình có thể nghiên cứu chúng thông qua các tool như audacity và sonic-visualiser
(Audacity và Sonic Visualiser là cả hai là phần mềm được sử dụng cho việc xử lý âm thanh và phân tích âm nhạc)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/05a8b8a3-616d-4f53-9fe8-1388949bc67b)
và đây là giao diện và dạng sóng audio của file 0000000039.wav
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/61402111-d2cb-4e2f-b1a5-76bd473b17a6)
sau khi chỉnh sửa để tìm hint ở cả 2 tool trên em vẫn không thấy được hint gì ngoài những hình ảnh trên
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ade29aeb-927f-4f7d-af2d-0355fd96a8a4)
và âm thanh chỉ có tiếng vỗ tay và reo hò của nhiều người
vậy hả năng nó sẽ ẩn chứa điều gì đó ngoài những âm thaqnh trên
em có đi hỏi được là mình có thể dùng một vài tool khác như DeepSound để kiểm tra những thứ bị ẩn trong file wav đó.
sau khi em tải về và dùng nó thì nó yêu cầu một password để có thể phân tích thứ bị ẩn từ file 0000000039.wav
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2617d56f-8940-4cf0-b4b1-4844e7fcb278)
em có tìm được trên mạng mình có thể dùng tool john the ripper để crack cái pass để truy cập vào đây 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/72e0c7eb-069c-47d8-95ab-75a1d4baa423)
em đọc được trên một trang là ubuntu tryhackme và thấy được thông tin về cài đặt john the ripper và cách để tạo các tệp nhị phân (trong đó có deepsound2john.py)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/cccf1bdd-8681-4d45-a8f3-630fb5f160c2)
và em tạo một hash pass để crack pass bằng john the ripper
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/5d8815ed-3836-4152-ad7e-875aaf6c7e8b)
bằng lệnh python3 /mnt/c/Users/MSII/Downloads/john/run/deepsound2john.py 00000039.wav > crakpass.txt 
chạy script deepsound2john.py để chuyển đổi dữ liệu từ tệp âm thanh có tên là "0000000039.wav" sang định dạng mật khẩu mà John the Ripper có thể sử dụng để thực hiện các tấn công
tiếp theo,để crack pass ta phải có một wordlist pass để bẻ khóa nó , đó chính là rockyou("rockyou" là một danh sách từ điển phổ biến được sử dụng trong các cuộc tấn công mật khẩu. )
em làm tiếp tục trên kali và đặt tên file là hashcrack.txt thay cho crackpass.txt
quả thật khi dùng lệnh "john -wordlist=/home/bawc/challenge/john/doc/rockyou.txt hashcrack.txt" thì nó đã crack được hash và có một pass được tìm thấy là ragerocks123
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/863f2154-f531-4c2a-b884-fdb9e348fb21)
sau đó em lấy pass nhập vào deepsound thì nhận được một file 2312.pdf
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/0bf46cf7-6330-44a9-9be1-1b04a89c7353)
và khi mở file đó thì em thấy có hình ảnh bên dưới
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f75a6ef0-8156-4e89-b7f9-b3f671406ed3)
em dùng strings để xem nội dung chứa trong file đó và có một đoạn text khá đáng nghi
nó có các funtion() và có các từ liên quan đến JavaScript, vậy có lẽ đây là một đoạn code của JavaScript .
sau khi sắp xếp lại nó và em chạy thử code nhưng không thấy điều gì đặc biêt.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/30c645ab-6ef8-44c0-82ac-c1e95bbfe660)
để ý đến các đoạn code phía dưới em thấy khá đặc biệt vì nó chứa các kí tự khá giống các kí tự mình có thể decode
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ae985e72-7449-4eea-bb01-baf23cdf01f1)
và khi em sắp xếp nó như trên và ghi ra được đoạn text này "IZWGCZ33IFZGKVKMN5ZXIP3"
em đã dùng cipher identify để decode chúng và nhận được flag là Flag{AreULost?`
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/500e3d57-9139-47f5-862c-2b640befadf8)
nhưng mà khi em nhập flag tren không được và em thêm thành Flag{AreULost?`} và đã đúng.
2.
