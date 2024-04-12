Q1:
dựa theo hint từ đề bài, e, có thể biết được nơi mà windows lưu trữ các thông tin của nó ở System32 và SysWOW64
( Systom32 nó chứa các file hệ thống gốc và các thư viện cần thiết để có thể chạy hệ điều hành windows
SysWOW64 là một tệp mà nó có thể chứa các tệp 32bit chạy trên hệ thống 64bit và đó cũng là tên gọi của nó "Windows 32-bit on Windows 64-bit" )
và theo đó em tìm được folder system32, và trong đây có 3 folder khác nữa
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/aa29ddd8-776d-4622-bde2-ce5282bfd385)
theo thông tin em tìm hiểu được thì với file winevt chứa các tệp ghi lại dữ liệu nhật kí sự kiện của hệ thống (hay có tên khác là Events Log)
còn sru thì chữa các tệp nhật kí và dữ liệu liên quan đến việc sử dụng tài nguyên của máy
còn đối với config , nó chứa các tệp cấu hình quan trọng cho Windows và cấu hình registry của Windows
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/0830a8d9-0d4d-4675-9eb9-424d1928de27)
và khi em xem các file trong folder config thì em thấy các file tương tự như vậy nên em export nó ra một folder khác để nghiên cứu nó
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2722c57a-3d7c-4af5-b311-b40ff4d9e1e7)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/832b8213-86e3-4645-ba5f-fe2696da7097)
và em mở các file export trên RegistryExplorer để nghiên cứu chúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8a04e1ca-33f9-444b-bc43-be7e50ac3b42)
và tại đây, em có thể tìm được current build number là 16299
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c35b2765-07f9-4c37-87ec-7c5771ff83f2)

Q2:
ta có thể dễ thấy được số users ở đây là 6 trong đường dẫn thư mục root\users
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2f48725a-f27d-4558-9122-14746819ca04)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/7940c03c-3aa0-461d-8c22-fbaf57db8e25)


Q3:
tại đường dẫn thư mục root\Users\hansel.apricot\Pictures\Saved Pictures, em có thể tìm được filename fruit_apricot.jpg
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d6589338-3194-4db7-b578-97f801e48324)
( CRC là phương pháp kiểm tra và phát hiện lỗi, được sử dụng trong các mạng số và thiết bị lưu trữ để phát hiện sự thay đổi tình cờ đối với dữ liệu được truyền đi hay lưu trữ. và CRC64 tạo ra một giá trị kiểm tra dài 64 bit, do đó nó cung cấp một mức độ bảo mật cao hơn so với các giá trị kiểm tra CRC ngắn hơn)
và em có thể tính toán hàm băm CRC64 online và em có được 2 kết quả là 07143AA2C080B345 ( với table type ISO ) và ED865AA6DFD756BF ( type ECMA )
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b60c0c0e-90eb-4b5e-aa28-29a4ff0c85e9)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b77de299-d150-4092-a21a-00903e43ba0e)
và em thử 2 đáp án trên thì nhận được kết quả là ED865AA6DFD756BF
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/aea11c2a-cf5d-445f-b185-63c6a38a87ee)

Q4:
tại folder picture của user suzy.strawberry em có thể xem properties của ảnh và nhận được file size là 72,448
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/208c113b-5d02-4270-bbe3-e29916d1d55c)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/26ea8f2e-ec9d-49de-8397-ab9c99f908e0)

Q5:
theo như hint từ bài cho, em tìm kiếm trong thư mục system\enviroment và tìm thấy thông tin của PROCESSOR_ARCHITECTURE là AMD64
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/ec35cd0f-4751-4f94-9e05-88c9353e22fc)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e5fb741a-cbf2-404e-837c-7809308a2817)

Q6:
sau một hồi tìm kiếm tất cả các user thì em không tìm thấy hình ảnh con chó ở user nào cả
để ý lại đề bại thì em thấy đề bài "là in their recycling bin" em tìm kiếm lại thì phát hiện có một folder có tên là $Recycle.Bin
và em tìm được ảnh có con chó trong một file ảnh tên là $RGETALS.jpg
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/956fda16-1ff3-4b7d-8a6e-b68e4d8580f0)
để biết ai là chủ của bức ảnh thì em có check properties và biết được chủ của bức ảnh này là hansel.apricot
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d34ce0d7-76bf-4986-998f-0233a9684278)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d59f87ab-4bdc-4c45-b2ab-4cb3e007ef73)

Q7:
em tìm thấy filename vegetable tại folder Picture của username : miriam.grapes
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/a96267d9-b4eb-4e43-81f1-08c0e9edb958)
để ý hex của file đó và em search trong file signatures và biết được đây là một file 7z (một loại file nén)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/36ce30c7-3831-454f-9206-e2a93e19c07a)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2591297e-7d12-4efd-8fe0-72f4dceafcd8)

Q8:
tại đây em xem các folder của user Miriam Grapes
và trong đống đó, tại một folder là root\Users\miriam.grapes\AppData\Roaming\Mozilla\Firefox\Profiles\9far2v52.default-release em ngồi xem các hex của nó thì thấy thông tin có vẻ sẽ liên quan đến đáp án
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/3fddbb96-5b80-4d69-bfba-1af061e4f9f4)
và em export nó ra và mở nó trên hxd, và em có nội dung : "what kind of phones do vsco girls enjoy"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c95a28b8-b278-4255-a280-5d74db6a1cdc)
và khả năng đối tượng mà Miriam Grapes thiết kế điện thoại cho chính là vsco girl
và đáp án chính là vsco
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/afc3a9d6-348b-4bfe-9c2d-8c1af19463d3)

Q9:
đầu tiên em nghĩ là mình có thể tìm kiếm theo các kí tự trên RegistryExplorer như device, devicename, name 
và khi tìm đến name thì em thấy có xuất hiện một computername : DESKTOP-3A4NLVQ
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e26a08a0-f284-4729-a4df-b13ab82ae8de)
và để ý thì em thấy nó khá giống với format nên em nhập vào và nhận được kết quả đúng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/1cce27af-11c1-439a-9d9c-27e27db938e5)

Q10:

Q11:
em kiểm tra các folder AppData của các users và phát hiện được có tổng 5 web browser là Chorme,Firefox, Edge,Internet Explorer,Tor Browser
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d6732d48-8569-4c40-802d-d73a61440667)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4422cf88-a5a6-49e9-996d-28220e2a646f)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/16b20b74-9f3f-4ab8-83cf-69f5a102a7a6)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2c14e213-62f0-4b64-b388-c791b8a65481)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/cdf2bc12-b1ec-4399-9a90-c7489c048989)
nên tổng sẽ có 5 web browser
Q12:
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b4aaf071-623f-46a2-8aa6-b4ffedf0d6e2)
em tìm được một file word trong từ folder Documents của User Tim
em export nó ra và khi mở nó lên em thấy 3 plan 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/737e59e3-2dad-41fd-8d1d-4e16ff9b60b5)
và khi em nhập vào đáp án là 3 lại nhận lại là flag invalid
có thể đã có plan bị ẩn đi, em thử đổi màu và nhận được thêm một plan nữa 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/178d9572-e2e6-4490-aa1f-825c58c067b7)
và tổng Tim có 4 plan
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/09753c70-f10a-4cdb-8071-54a99a059850)

Q13:
dựa vào plan bị ẩn được tìm thấy thêm ở Q12 thì em biết được người bị sa thải chính là Jim Tomato
•	Fire Jim Tomato
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/92b263da-b438-415d-945e-bd75b8de3303)

Q14:
em tìm được nơi xác định người dùng cuối cùng 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/13ebea9a-d5ee-4d9c-9aef-0cc757b1b425)
và dựa theo thông tin đó, em tìm folder WinLogon trong RegistryExplorer và tìm được thông tin của người đăng nhập cuối cùng chính là jim.tomato
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2ed22c71-fc3a-4bab-ac9e-ac75c6f498ae)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/955ba589-8bdf-40f3-97e1-af9d71074ac3)

Q15:
dựa theo hint của bài thì em đi theo đường dẫn và tìm được folder places.sqlite và em export nó mở trên Sqlite
ở đây em thấy thông tin trong bảng moz_places có chứa thông tin liên quan đến đáp án
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/1602e054-6618-44ac-9451-37c26be6e300)
em thấy lịch sử tìm kiếm của Tim có những thông tin như flirt with women với có thể là lời khen "Your Secretary Is Cute"
và có khả năng người mà Tim tán tỉnh chính là thư kí của anh ta  --> đáp án chính là Secretary
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/434c7959-d1eb-434d-a902-5779b6978568)

Q16:
dựa vào hint về link dẫn folder của bài, em tìm được folder Sam
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/64321241-70d3-43fa-af56-6e32a8376aef)
tại đây có 2 folder là Aliases và Users và em kiểm tra cả 2 folder trên
ban đầu em kiểm tra folder Aliases thì không có thông tin gì liên quan đến SID , nhưng ở cuối nó lại xuất hiện thêm 2 folder là Members và Name
em lại tiếp tục kiểm tra nó, nhưng ở đây em thấy tại Folder member xuất hiện một mã SID 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/bc54f19b-13ed-4796-b948-3d9fc7c7fccb)
và có thể nó sẽ liên quan đến một cái gì đó.
và em kiểm tra các folder khác trong folder Aliaese cũng k có gì đặc biệt
Đến với folder Users thì em thấy nó có xuất hiện một cái bảng như sau :
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/50e8579c-e325-4b52-8fff-d7ecdc864fd5)
tại đây, em thấy user id : 1004 của user "suzy.strawberry" khá là khớp với format của bài
và em tìm hiểu thì đây cũng là một loại SID nhưng nó là một phần của SID và đại diện cho một nhóm người dùng hoặc một người dùng cụ thể trên hệ thống
ví dụ như S-1-5-21....... có thể được rút gọn lại S-1-5-21-A (A là một số cụ thể) và A sẽ đại diện cho một user hoặc nhóm người trong hệ thống
và khi em nhập vào thì đúng đáp án là 1004
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/aeaa5a03-3b16-417e-91a9-c71498cd4270)

Q10:
dựa vào câu trên về SID thì em có sử dụng mã SID tại folder để nhập vào Q10 thì ra được đáp án của câu này
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/bb9a6d65-1026-4e40-a76b-dfd5da52b88c)

Q17:
tại đường dẫn thư mực root\program1\torbrowser em tìm được folder tor
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c5568cd5-23aa-47c1-ab04-85a07e7e2433)
để ý format của link dẫn thì có lẽ sẽ là ổ đĩa xong đến folder nào đó, nên em sẽ thử các đáp án và cuối cùng em ra được là C:\Program1
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/390925fd-be50-4864-929b-e2a73d032218)


Q18:
để biết được lịch sử duyệt web của một trang thì em có research và biết được location của nó như sau 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4f195077-0386-4acb-96d1-ecf0ac0ce5b9)
và em thử tìm kiếm theo location đó và tìm được đúng theo format của chorme
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/6fd7f1d9-0f6e-4a30-9ce4-e5671f6be123)
tại đường dẫn root/Users/jim.tomato/AppData/Local/Google/Chrome/UserData/Default/ và em đã tìm được file history tại đây
em export nó ra và mở trên SQLite và tìm được url của ytb là "https://www.youtube.com/watch?v=Y-CsIqTFEyY"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/04131f2d-ba80-489c-8280-44d7db03cae1)

Q19:
sau khi kiểm tra các folder của các users thì em phát hiện ra có filename LibreCAD trong folder Downloads của miriam.grapes
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e6a7b9d4-21ce-4b92-9cb5-a5d91ba0d77c)
nên miriam.grapes chính là người đã tải xuống  LibreCAD
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/74028f6c-eb88-478f-87b1-92358f53a0e2)

Q20:
em research được là thông tin đăng nhập của người dùng thường được lưu trữ trong tệp "SAM" 
nên em sẽ nghiên cứu file này.
em dùng regripper để xác định các hoạt động login của users
em dùng lệnh regripper -r SAM -p samparse
và kết quả của em khá nhiều các thông tin login của các users
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2a2043d1-014f-44a1-a285-b28ecd7203cf)
và tại đây em thấy được số lần login của admin là 10 
và đó cũng là đáp án của câu này
Q21:

Q22:
em truy tìm đến phần Pictures của Tim và thấy được một hình ảnh quả táo ở đây
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/58dee0e0-3c6b-413e-bc52-c7fe85b79850)
và dựa vào thời gian ở properties thì em có kết quả là 04/05/2020 03:49
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/0338783c-ebe9-4b8a-9baf-87c708b7158c)

Q23:
theo như hint từ đề bài là phân tích ntuser.dat từ user Jim thì em tìm được nó và export nó để chạy trên RegistryExplorer
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8218fa70-1a4b-4f4c-a312-ea35c7b62e9b)
và tiếp tục theo đường dẫn folder của bài thì em tìm được hoạt động khởi chạy các web và em thấy việc khoier chạy torbrowser 1 lần nhưng em nhập vào lần thì không đúng
em thử nhập là 2 thì chính xác
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/b5a16e2a-8d78-42af-9fb1-af47b4568e01)

Q24:
tại folders Downloads của user miriam.grapes và trong đó chứa hình ảnh của chiếc điện thoại
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8d91e23a-eb64-407a-b312-57324443d3d8)
em export hình ảnh này ra và xem thông tin cảu nó.
nhưng để ý kĩ lại đề bài thì nó yêu cầu là file png , nhưng khi tải về em thấy lại là file .jpg nên em đã check hex và thông tin cảu file này
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/710a7b4a-7b6c-4b06-9ec7-ba74d9faa736)
và đây là thông tin em nhận được
và em dùng lệnh ls -al thì thấy file này có lượng dung lượng khá lớn nên có thể nó sẽ chứa dữ liệu ẩn gì đó
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/7d2f41ec-a7fe-43d6-816b-da4094863739)
khi em chạy lệnh foremost thì em thấy có xuất hiện một directory png, em truy cập vào nó và thấy một file png và đó là một chiếc ip
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8b1482d9-52c2-41fd-b3c9-02bf072177e5)
và có lẽ đây chính là thứ em cần tìm. Và em dùng lệnh sha1sum để kiểm tra mã băm sha1
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f166cd81-293f-4a32-b165-bbf6563568f5)
và kết quả chính là : 537fe19a560ba3578d2f9095dc2f591489ff2cde

Q25:
theo em tìm hiểu được thì mình có thể check last opened tại folder Recent 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/6024dfb1-4a3e-4dc0-ab3e-d39a14c0a114)
nên em đã tìm kiếm Recent trong RegistryExplorer và em tìm được một vài thông tin liên quan đến nó
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f682f78a-d0bb-465e-a7d3-e7cecf9e9699)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/a8edbe31-004a-4505-b9ac-3200d230d5d8)
và em thấy được lần cuối mở file chính là vào : 2020-04-11 23:23:36
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4743c131-0692-4325-8262-908d7d083aa2)

Q26:
em tìm thấy file $MTF tại folder root
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/687ba48c-db0c-4a0a-bb3f-781014cf0010)
em chuyển nó vào cùng với folder chứa mtfdump.py em tải về
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9d8ff56a-c2e8-4337-a63c-6365d316fd45)
và khi em chạy lệnh python3 mftdump.py '$MFT' thì có vẻ như nó bị lỗi gì đó
em copy lên chatGPT thì nó báo là có thể nó không đúng phiên bản nên em đã dùng python2 thay vì python3
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d82c3db8-3b10-4c1f-8fe2-3d1b41da69ae)
và khi em chạy lệnh python2 mtfdump.py '$MFT' thì chạy liên tục không dừng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4ac0aa5e-ffaa-4f56-b2eb-07ac70e94bcf)
nên em đã chuyển nội dung khi chạy lệnh đó vào file.txt và sử dụng cat 'file.txt' | wc -l file.txtv
để xem số dòng ( hay số mục của MFT )
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/93e6f625-1753-46cf-8fbe-aef7b04c439a)
và em có kết quả là 219906, nhưng khi nhập vào thì kết quả lại báo sai, em kiểm tra lại file đó thì 2 đoạn đầu của file sẽ không tính vì đó là trường tên các cột và dòng thứ 2 là các dấu gạch ( nên không được tính là các mục của MFT)
neneloaij bỏ 2 dòng đó thì em có kết quả là 219904
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e2ad341b-5354-40b5-a39f-6ddab56cbfd3)

Q27:
dựa theo hint từ đề bài thì em có thể là Tim sử dụng nên có thể trong lịch sử sử dụng avf tìm kiếm có thể sẽ có thông tin gì đó, và em tìm được file hsistory ở folder Details
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/fafc2d91-092e-4731-aa86-24e27b34857f)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/43fa47d5-f632-4c31-a491-144483e0235f)
và em export file history và mở nó trên SQLite và phân tích nó, tại url gg em thấy một thông tin khá quan trọng
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/40e06314-3502-4c23-bd28-35a2ba225c94)
và nhân viên của anh ta có một mùi gì đó khá khó chịu nên Tim search tìm cách để sa thải anh ta vì anh ta bị "stinky"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/357fef0e-8ca3-42f1-96bd-59bee94e9ab9)

Q28:
em có thể thấy được đường dẫn folder liên quan đến việc "Quản lý các chương trình chạy khi khởi động Windows"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c70c8eaf-91fa-42e1-ad4b-d5e91d718ba8)
vì bài yêu cầu với user admin nên em sẽ export file NTUSER.dat của users này (vì file này chứa thông tin cấu hình và cài đặt cá nhân của users này trên máy tính)
và em tìm kiếm theo đường dẫn em tìm hiểu được và phát hiện ra dịch vụ đám mây ở đây chính là Onedrive (một dịch vụ đám mây cảu Microsoft)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/0748815a-7223-4f41-aa8b-c6ba14e4d570)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4f5a31d7-d4e8-4067-a5a3-5a701b9e96d2)


Q30:
em có thể tìm thấy "Địa chỉ IP của cài đặt Ethernet của tôi được lưu trong Sổ đăng ký ở đâu"
HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/a547644f-7162-4300-a9e4-39d0413d1173)
tương tự như những câu khác thì em tìm kiếm theo bộ lọc vầ tìm được một bảng các ip sau 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/50ec3dc3-e4b0-4322-91fd-cda0b5825c57)
và đề bài hỏi ip address nên đáp án sẽ là : 192.168.2.242

Q31:
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/981fc978-f4bb-418d-a570-fb2abe995344)
em có thể tìm được location của nơi lưu trữ những mục được ghim vào thanh tác vụ của họ
<user dir>\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch\User Pinned\TaskBar
và dựa theo đó em tìm được folder chứa các mục được ghim 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d4e357c5-1dc2-4247-8a52-b09d542f3df2)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/22ba6c56-66b5-4f61-8d2c-f6379b815478)
em thấy nó đều liên quan đến admin nên có thể nó sẽ là đáp án của câu này
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/7866dc7d-bc12-4794-85c8-826e2ffbc29f)

Q32:



