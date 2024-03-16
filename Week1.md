Q1-WebStrike
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c12ce469-401b-4994-9750-95e154c3f6b6)
khi mở wireshark ta có thể thấy được các ip và ta có thể check ip của 2 địa chỉ ip là 117.11.88.124 và 24.49.63.79
khi check 24.49.63.79 ta biết được city là Hagerstown nhưng khi nhập vào đáp án --> sai
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/3af0da1c-4d4c-47a3-91d1-657d63ceb54a)
check tiếp ip 117.11.88.124 ta thấy đc là tianjin và khi nhập vào đáp án --> đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b9070b2b-343f-45a5-adec-746b2b160f13)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ad901da1-a6dd-4cf0-b8a8-08383d949b04)

Q2:
ngay cột protocol ta có thể ấn vào HTTP hoặc TCP và chọn Follow --> TCP Stream để xem cuộc trò chuyện TCP giữa máy chủ và khách
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/dbb920dc-353a-4501-8332-37b4203cf739)
và check tất cả các phương thức HTTP và TCP ta đều thấy:
User-Agent : Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2a9c7032-a498-4325-ba9b-dd92a8dfe3f3)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d2e71069-6b7e-4593-954d-2fd8f98bff79)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/775fd253-472b-4fce-8334-375e3c37e0f2)
Và khi ta nhập kết quả thì phù hợp với Format
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/cf51bfdc-cdbf-44f7-8fd3-2725481405e1)

Q3:
Sau khi check file có cổng PORT ta thấy ngay tại mục "Content_Disposition" ta thấy một filename là : "image.jpg.php" và "image.php"
Đây có thể là một tệp script PHP thay vì một tệp hình ảnh hợp lệ và nó chứa phần mở rộng thực thi như php và có khả năng tạo ra những rủi ro bảo mật nghiêm trọng, như thực thi mã từ xa.
Ta thấy filename "image.jpg.php" đang ở dạng đúng với format nên ta nhận image.jpg.php làm đáp án
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8cdfeacb-9d48-47b0-9804-c11a6edea361)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f8c96f21-e9aa-4dbc-9aaa-6c8cf712d669)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b3848a0f-bd66-4528-a1d1-c6cafe41a605)

Q4:
sau khi check một vài file liên quan đến uploads em thấy chúng đều có các mục là "Referer: http://shoporoma.com/reviews/uploads/"
để ý đến format ta thấy /reviews/uploads/ rất phù hợp nên ta điền vào format và nhận lại kết quả đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2e43eaa7-26a7-4d5c-8cde-88ea6cd784f1)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/963ff652-029f-4876-a0e8-5a842dee6fd3)

Q5:
Ngoại trừ các cổng 80 hay 443 được sử dụng cho web shell độc hại thì cũng còn cổng 8080 có tác dụng tương tự như 2 cổng 80 và 443 :
+ tránh bị phát hiện từ các biện pháp bảo vệ
+ lưu trữ và triển khai mã độc
+ thực thi các lệnh bất hợp pháp
+ kết nối từ xa
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/81260c34-e832-43b6-b030-7fddb3f12b65)

Q6:
đầu tiên em lọc giao thức HTTP trước để tìm các gói tin liên quan đến giao thức này
em thấy PORT khá ít nên em check phần này trước ,và khi truy cập vào gói tin "POST / HTTP/1.1" thì thấy đường dẫn /etc/passwd ngay ở mục đích đến (là phần chữ xanh )
nên có thể có người đang muốn truy cập ,đọc hoặc lấy đi file passwd --> passwd là đáp án
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d68f6d72-29d3-4c65-a8bd-85f5bc59491d)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/dda50807-409f-4f7c-8074-1a346f2063ac)

Q1 - Poisonedcredentials
Sau khi lướt một lúc r em thấy các phương thức LLMNR và MDNS đều có cụm query ... fileshaare nên em thấy khá là nghi ngờ,
khi em xem file hex của chúng thì đều có đoạn đầu khá giống nhau 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/601c8952-8b9c-4192-80d3-35af9ef10526)
còn em để ý một gói tin có giao thức NBNS thì thấy có duy nhất một gói tin với infor "Name query NB FILESHAARE" và đặc biệt là đoạn hex đầu của nó lại khác biệt hẳn với các gói tin còn lại nên em nghĩ nó là đáp án
nhập vào kết quả thì em nhận được kết quả đúng.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/fc4f90fd-077e-44cc-8d1a-a031805bb244)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4c608e6b-e655-4b2c-9b03-80e771c7e380)

Q2:
ngay dưới đoạn infor tìm được filename trên em thấy một gói tin với nội dung Name query respone NB 192.168.232.215" em cũng đặt ra sự nghi ngờ với nó.
và em nhập vào đáp án thì thấy nó đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2a406e85-6171-43a1-ab30-de91c59f270d)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f5d36468-a7f0-4e05-99bb-467a642d180a)

Q3:
khi biết ip của máy lừa đảo thì em lọc ip đó ra và thấy Destination ip có 2 ip là 192.168.232.162 và 192.168.232.176 . 
em thử lần lượt 2 ip thì nhận được đáp án là 192.168.232.176
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9cc7763f-7644-4924-b1b6-2dab3294ebdd)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8eed47b6-d99a-48db-a031-c226c97aca8e)

Q4:
để thuận tiện cho việc tìm tên người dùng em dùng bộ lọc để lọc từng giao thức rồi xem thông tin
em lọc đến SMB2 thì đọc được 1 gói tin có "acct:janesmith" ( có thể hành động được thực hiện bởi ông này nên ông janesmith sẽ là user) và từ đó em nhận được đáp án.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/dec35bf9-ebb5-4f69-8778-745b30dc4fc9)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f54153f9-475d-4c4c-a5fc-022832a2775d)

Q5: 
em dùng bộ lọc , lọc SMB ,SMB2 để tìm máy chủ
khi lọc SMB em chỉ thấy 3 gói tin và đều k có thông tin của máy chủ
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/a65691be-5c11-4f4e-80e1-199adc443014)
em tiếp tục lọc đến SMB2
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/06aa71d7-bd5e-4a62-8673-38ed09824ddb)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c7d6972a-1c3b-4d7d-92f7-7aaa5c04af00)
thì em có thể tìm được thông tin của NetBIOS computer name : ACCOUNTINGPC như hình. --> và đây hoàn toàn khớp với đáp án.

Q1 - Openwire.
sau khi đọc thông tin từ một gói tin của giao thức HTTP và có tên như hình em thấy HOST : 146.190.21.92
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b148a560-4cc6-4b1c-8466-c13ccc99e9e4)
và em nghi ngờ đây có thể là đáp án và khi nhập vào để check đáp án em nhận được đây là đáp án đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/0647cca3-1a30-4784-8e6a-2e859d5fcdb6)

Q2:
em xem thử các port của các gói tin (gồm Src port và Dst port) và em nhận thấy có một số gói tin đầu có sự khác biệt khi có port 61616 và 47284 ,nên em sẽ thử 2 port này và nhận đucợ đáp án là port 61616.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/567a305d-056e-4849-bb24-e998c2e5a555)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/73875192-1f22-4997-82cd-f115ea1ead1c)

Q3:
phần này sau khi lọc rồi tìm kiếm thông tin trong wireshark của các gói tin trong đó em k thấy hint gì về dịch vụ đó nhưng khi xem thông tin của cổng 61616 thì em thấy Cổng 61616 thường được sử dụng cho dịch vụ Apache ActiveMQ.
em thử nhập đáp án là dịch vụ kia thì đúng ạ
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/12fd2d42-25f9-4105-8664-412f106b4c9b)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/a82bbeaa-765d-484d-9098-72ba02ff3dcc)

Q4:
sau khi lướt các src port và dst port em thấy port 128.199.52.72 khá được thấy như các port 146.190.21.92 và em nghĩ có thể nó là ip thứ 2 của máy chủ c2 
(còn port 84.239.49.16 cũng được thấy khá ít nhưng em nhập vào không đúng với đáp án của bài)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/325b0aff-916f-4710-a5cd-a4a901ef6cf8)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/79e77640-1b12-40e4-afcf-227de0b45608)
và khi nhập vào em nhận đc đáp án đúng là 128.199.52.72

Q5:
đầu tiên em lọc giao thức http trước để xem thông tin từ chúng.
để các các giao thức này em thấy được 2 tên là invoice.xml và docker.
em thử cả 2 tên và nhận được kết quả là docker
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ea45358d-c40b-4b42-9817-04095966c03e)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f8e7fa11-634c-4882-bb33-06ab84a3331d)

Q6:
đầu tiên em lọc các giao thức http để phân tích.
em đọc gói tin có stt thứ 11 và tìm được thông tin là " <bean id="pb" class="java.lang.ProcessBuilder" init-method="start"> "
và Java class ở đây chính là "java.lang.ProcessBuilder" 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/cd66cda8-849d-4641-a7ff-6a90d0011b82)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9c2afe10-8801-4b7a-9bd4-75d53efcf39f)

Q7:
em tìm kiếm trên mạng về mã định danh của nó :CVE identifier associated with the java.lang.ProcessBuilder vulnerability
và có kết quả là : ![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/86c83ea6-11dc-49ee-87e7-1c9a627128c2)
và nhập vào kết quả : CVE-2023-46604
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d1d8dd02-39db-4047-907b-5617f40d12f7)




