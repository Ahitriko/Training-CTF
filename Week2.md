Q1 - Psexec-hunt :
đầu tiên em sử dụng tính năng Statistics -> Endpoints để xem tất cả ip xuất hiện 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/faae0d10-bd39-41e2-86a8-f51d315a038a)
và em thử nhập các ip có trong đó vào và có đáp án đúng là : 10.0.0.130
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9539cc6b-41f2-4675-896a-06065d288b94)

Q2 :
đầu tiên em lọc tên máy chủ của kẻ tấn công tìm được ở Q1 và giao thức smb2 để tìm thông tin:
em tìm được một thong tin có NetBIOS name là SALES-PC và target name cũng là SALES-PC, mà nó cũng có formagt giống đáp án nên em nhập vào thì nhận được kết quả đúng.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d1341df1-86df-4c90-b86f-625336389b6f)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9d8d4d34-8b93-43a4-b160-a26396f3456b)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e5ca3620-777f-4357-a4ac-d3be2e9f5ce5)

Q3:
ngay trong gói tin em vừa tìm được ở Q2, em cũng có nhận được một username là ssales .
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c3bdfa17-ad37-41ba-81b6-795600ab88aa)
và khi em nhập username đó vào đáp án thì đúng .

Q4:
để ý các gói tin em thấy có các thông tin liên quan đến PSEXESCV nên em có tìm hiểu thì biết được đây cũng là một dịch vụ dùng để thực thi các lệnh hoặc các chương trình trên các máy tính từ xa trong mạng máy tính
nên em đã nhập nó vào đáp án và có kết quả đúng.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/cd98abff-76cd-46ea-a7ac-cf63ece83986)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/fc32bec5-5b71-40e2-802d-1c4794121e48)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/19d14820-2426-445e-915a-1fa375ae6ac7)

Q5:
em check một vài gói tin và nhận được thông tin giống format đáp án là ADMIN$ 
ADMIN$ :là một tài nguyên chia sẻ mặc định trên các máy tính chạy hệ điều hành Windows trong mạng nội bộ. Nó thường được sử dụng cho mục đích quản trị từ xa và chia sẻ tập tin.
nó cũng khá giống yêu cầu của bài nên em nhập vào đáp án và nhận về kq đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/23561b0e-c232-42fa-93a5-1a3bd1a40293)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/46fc57a0-48e7-4c1a-a62b-186a0fb130c1)

Q5:
đầu tiên em lọc giao thức SMB2 và em tìm thông tin từ một sooss gói tin có xuất hiện thêm một thông tin là IPC$
IPC$ là một tài nguyên chia sẻ mặc định trên các máy tính chạy hệ điều hành Windows trong mạng nội bộ ( theo em tìm hiểu trên chat gpt)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d042a620-c54b-45f4-80be-99b6d6ba85f2)
và khi em nhập nó vào đáp án thì hoàn toàn đúng.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e4b5a045-3eed-44a3-b62f-3100929c902f)

Q6:
khi em dùng bộ lọc để lọc giao thức BROWSER để tìm kiếm thông tin thì có phát hiện sự liên quan đến MARKETING_PC nên em nghĩ nó chính là đáp án của đề bài
và khi em so nó với format đề cũng giống nên em nhập nó vào đáp án.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/a132000a-028f-49de-8031-3a1895fa1f25)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/caac5f1e-0197-4e6e-ba7f-3946d877bba4)

Q1 - The Crime.
sau khi mở file trên ALEAPP em thấy ở mục app icons có một số app nhưng để giao dịch thì có lẽ sẽ dùng đến app Olymp Trade nên có thể nó chính là đáp án.
và khi em nhập tên nó vào thì đúng là nó.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b46eb508-39d2-4759-8b8e-5fcab22ee3c9)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2ad6599e-12f4-4df5-8922-9e347723bf62)

Q2 :
em nghĩ nếu nạn nhân nợ thì có thể sẽ có thông tin qua tin nhắn hoặc thông báo một app bất kì nào đó
sau thời gian tìm kiếm thì tại mục SMS messages có thông tin về số tiền :
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/108ab93a-1017-48ec-99da-bb4027033d9d)
và nhập số tiền vào đáp án thì hoàn toàn khớp.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/3301ac1f-8693-4821-90fa-de65908a94e3)

Q3:
sau khi xem được số khoản nợ thì em có thể biết thêm thông tin là số điện thoại của người kết nối với nạn nhân là +20 117 213 7258
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/cb46d28e-adc7-42b8-9de3-1e726b445054)
sau đó em tìm kiếm tại mục contacts để xem thông tin người đó là ai và biết được tên họ là Shady Wahab
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c3cbcea6-207b-4b62-9b5a-37ce93cfc98c)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/3f69ff61-c8f1-4cae-9663-a1e523c7dde0)

Q4:
em tìm đến mục image manager cache và thấy được vào ngày 20/09/2023 nạn nhân có chụp ảnh tại một nơi như ảnh
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/31a357ce-d512-4583-9540-2ec58baacc2f)
em dùng gg image để tra cứu thì biết đây là một khách sạn tên là "The Nile Ritz-Carlton"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f3904a6d-0950-43d2-9ae1-26a2dd8afe9c)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2214554a-63ba-4c37-9cff-e64b9ef01d22)
và nó là đáp án của q4
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/6cd8b3f0-ee47-45c1-a4ee-7965ae663bce)

Q5:
em thấy địa điểm gặp mặt của 2 người tới là The Mod Museum nên em có tra ra nó là một bảo tàng ở Las Vegas
nên em nghĩ có thể đây sẽ là đích đến tiếp theo của nạn nhân và em nhập vào đáp án nó đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e760b100-5746-4974-b5fb-78328014eda5)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b9c6e2f9-c71d-436b-8872-961376bf47a5)

Q6:
sau khi em vào discord chat của nạn nhân em thấy được cuộc trò chuyện giữa 2 người và có hẹn nhau đến một địa điểm là The Mob Museum
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b28c1bf6-c1aa-42ad-99b4-d90213dd6907)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/6a3726d7-1900-49ca-adb9-38454988718a)

Q1 - SpottedInTheWild:
sau khi giải nén file bằng rar, em nhận được một disk và khi em dùng password để mở nó thì em thấy xuất hiện rất nhiều thư mục.
em mở nó trên FTK image (1 tool có khả phân tích ổ đĩa và dữ liệu)
tại đây em có tìm được một thư mục Downloads và ở đây, em thấy có một folder có tên là telegram desktop
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ada0c025-b4c9-4178-81e2-0cb50feae049) 
ở trong đó có những file có tên là SANS SEC401.rar
theo yêu cầu của bài thì đi tìm một file được tải xuống nên em nghĩ có thể là sanssec nhưng em nhập vào lại không đúng
để ý về trước thì em nghi ngờ về telegram desktop (telegram nó cũng là một ứng dụng nên em khá nghi ngờ nó)
và khi em nhập nó vào thì đúng với kết quả
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/631220c0-34bf-4cd9-953d-2dd0cb952f1b)

Q2:
đầu tiên em có thể xem properties của file này em thấy được time create là 03/02/2024 2:23:20 PM nhưng em nhập vào không đúng 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f5886ce2-ecc9-4b21-a8ae-fbb680cb9d0f)
tương tự như vậy, em cũng có thể view properties trên FTK imager và em thấy được time create của nó khá khác biệt so với em xem trực tiếp ở file
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/930ae76f-8045-4120-a05e-5551cce5c47d)
2/3/2024 7:33:20 AM là time mới được tìm thấy
có thể là timee đã được thay đổi, và khi em nhập vào time trên thì phù hợp với đáp án
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/5b4c0b2b-eefc-4ab6-88fd-f7c9a8bb856d)

Q3:
để ý ở đây em thấy được file độc hải được tải về là dạng rar, thì khả năng lỗ hổng chính là liên quan đến nó
em có tìm kiếm được thông tin về loại lỗ hổng CVE liên quan đến loại file rar thì có một loại định danh CVE là CVE-2023-40477
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/713a107f-9333-4f54-aed8-0f2d47216459)
em nhập vào nó không chính xác nên em tiếp tục tìm kiếm những loại định danh CVE khác và em tìm được một định danh CVE nữa là CVE-2023-38831
CVE-2023-38831 có thể giúp kẻ tấn công có thể khai thác lỗ hổng này bằng cách tạo kho lưu trữ RAR hoặc ZIP đã sửa đổi chứa các tệp độc hại, điều này có thể dẫn đến việc thực thi mã tùy ý
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/93b8c90c-5579-403e-8e5e-f95691cd5ead)
và đó cũng là đáp án của câu này
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2182fb91-7118-4c22-9745-fec7f6a39203)

Q4 :
đi nghiên cứu tiếp về file SANS SEC401.rar, em có thấy thêm một file dạng khá kì lạ , đó chính là SANS SEC401.pdf .cmd
( đối với file .cmd ,nó có thể được sử dụng để triển khai các hành động bảo mật, kiểm tra lỗ hổng, thực hiện các tác vụ tự động hoặc thậm chí là để thử nghiệm các kịch bản tấn công trên hệ thống Windows và có thể chứa các mã độc hại và tệp lệnh nguy hiểm)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b23420c2-1792-4aaf-a16b-8798a17c3643)
và SANS SEC401.pdf .cmd cũng là đáp án của câu này
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/11019321-f583-4f2d-8aad-8e6d444c7b5b)

Q5:
khi em mở file trên trên cmd thì em thấy khá nhiều thông tin kì là , nhưng khi để ý thì em thấy có một url như sau
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/5c7b85b5-1955-4391-8c4e-b29be874d1c7)
và đó cũng chính là kết quả cảu câu hỏi này 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2fde6cc8-cd34-4091-9d93-ff082c3f4bad)

Q6:
