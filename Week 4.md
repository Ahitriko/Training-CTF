Q1 :
đầu tiên em dùng plugin "pslist" để liệt kê các tiến trình trong bộ nhớ với lệnh "python3 vol.py -f memdump.mem windows.pslist"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/baefc00a-4a95-4829-b191-48826c0bb995) 
sau đó để ý các file ở đây em thấy có rất nhiều file 'svchost.exe'
em grep tên file và để ý một điều là ở đây có các PPID được lặp lại là 804 và 4824.
(khi em chạy thì có 2 cột đầu sẽ là PIP và PPID : PID cho biết vị trí của tiến trình trong bảng tiến trình của hệ thống còn PPID thường được sử dụng để theo dõi mối quan hệ giữa các tiến trình)
( khi một tiến trình con được tạo ra bởi một tiến trình cha, PPID của tiến trình con ,còn PID là tiến trình cha)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/7a6d2ccc-84fc-43b9-9e30-b3314c43bbc5)
em có lọc thử 2 PPID đó ra và thấy rằng thấy 804 và 4824 đều là tiến trình gốc và nó tạo ra rất nhiều PPID 804 và 4824 được tạo ra từ PIP gốc.
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/349149a9-69d3-44fe-9252-76bec1549498)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/bae60d3f-c280-4b98-bbd6-24e72845f4b1)
và em có tìm hiểu được là điều này có thể gợi ý về sự bất thường trong hệ thống
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/eae2dc80-31ed-482b-8335-bfb3275bb72e)
và em thấy 4824 có vẻ giống flag hơn. Nhưng khi em nhập vào lại thông báo invalid flag.
quay lại với 4824 em có để ý được nhưng điểm đáng ngờ
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/3cb905d0-0898-4399-940b-61b81331a3d6)
ở đây em thấy các PIP vẫn chưa kết thúc tiến trình đang chạy
em liệt kê chúng ra và nhập vào flag và kết quả chính là 8560
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/da0e3919-0a8c-4791-a326-604aa213356e)\

Q2:
theo hint từ đề bài, chúng ta có thể chạy plugin 'memdump' , nhưng với phiên bản volatility3 thì chúng ta có sự thay đổi
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/25880ce9-bcff-4a6d-957f-80ba6b4cba8b)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/188c74d7-2bd7-498b-a5d4-220c6e30c623)
và đây chính là sự thay đổi giữa 2 phiên bản 2 và 3 của volatility
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/3bfd95a8-99bb-4edb-84ee-17a6833518e0)
áp dụng vào bài thì sau khi em chạy lệnh thì nó có xuất hiệ file là 'pid.8560.dmp'
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8c7364ca-2949-45c8-8c49-069f6ee40d78)
tiếp đó em dùng 'strings -n 32 pid.8560.dmp > 8560.txt' để in các strings trong file pid.8560.dmp (với 32 kí tự để thỏa mãn độ dài của hàm băm md5)
sau đó em sẽ dùng lệnh cat để đọc nó. Tuy nhiên ,em thấy nó khá dài và khá nhiều nội dung
nên em sẽ chuyển sang dùng cat '8560.txt' | more để từ từ xem nội dung của nó.
và em thấy được thông tin khá hữu ích là một đoạn flag dạng base64
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/2cec7e2e-e74b-48ae-931b-ba25a473bf93)
và khi decode nó em được một hàm băm md5 là :3a19697f29095bc289a96e4504679680
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4ebd86ae-cac9-4bad-9c8e-16469af6ef7c)
và nó cũng chính là đáp án cần tìm
Q3:
ngay từ Q1 ngay khi chạy lệnh python3 vol.py -f memdump.mem  windows.pslist.PsList | grep '4824' ở bên Q1
em có thấy ngay ở đầu chính là tên tiến trình của tiến trình gốc độc hại "explorer.exe"
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/e949f114-f0d2-4400-88fd-7f25ea3c7054)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/6b89c337-4274-436d-8389-44eed497bc4e)

Q5:
sau khi tìm hiểu thì em thấy mình có thể sử dụng plugin 'mftparser'thì em có sử dụng nó để chạy để phân tích các mục MFT tiềm năng trong bộ nhớ. 
nhưng mà có vẻ phiên bản của volatility3 không sử dụng được plugin này
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/8944b993-764f-4371-bdbb-555188215c02)
để ý lại format của đáp án chính là file .txt nên em có thể grep cụm này trong việc tìm kiếm
strings memdump.mem | grep -F '.txt'  
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9e94c5d0-ae62-48f6-bfde-10d342b6a3b7)
sau đó em thấy khá nhiều tệp dạng txt như test.txt , và trong các filename em tìm được filename khá phù hợp với format đáp án
đó là file yes.txt
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/4ecdd086-d740-46a6-982f-890d1283e67e)



