Q1
đầu tiên em xem danh sách các địa chỉ ip và ở đây có duy nhất ip có format cùng dạng với fomrmat của đáp án là :111.224.250.131
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/50dddcd6-558a-459c-9f94-49398105f33e)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/d0c4e90e-7522-4e72-81a5-73997e37112d)

Q2:
sau khi biết địa chỉ ip , em có thể tìm thông tin về ip này tại Ip address lookup
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/332e9ac8-be68-4dba-942d-61cf1b0b50af)
và em thấy được địa chỉ của nó chính là Shijiazhuang
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/db8dc9d0-69b6-42dc-bea6-287390d40ef0)

Q3:
đầu tiên em lọc phương thức http và để ý thấy có khá nhiều các cụm search.php và nó khá giống với yêu format của đáp án và em nhập nó vào đáp án thì chính xác
có thể đây chính là file mà kẻ cắp đang muốn truy cập và khai thác thông tin từ nó 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/c87148bf-64a4-4f0e-b2a0-cc49fa27d449)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/5a4e8a23-2a41-4d5d-a144-b6c90ba100a1)

Q4:
dựa vào lọc các phương thức http bằng method POST và GET kết hợp format của đáp án , em có thể thấy cụm
/search.php?search=book%20and%201=1;%20--%20- khá nghi ngờ về nó 
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/84a12b32-e16f-487c-baee-73db9ad189e2)
và em nhập nó vào đáp án thì chính xác là nó
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/9d09d755-888f-4476-b4a2-91840120c768)

Q5:
tương tự như Q4 thì em tiếp tục tìm kiếm khi dùng bộ lọc để tìm kiếm request URI
và chúng khá nhiều thông tin và khó để chọn lọc, nhưng dựa vào format của đáp án , em có thể thử những thông tin đó.
và em tìm đc nó chính là 
/search.php?search=book%27%20UNION%20ALL%20SELECT%20NULL%2CCONCAT%280x7178766271%2CJSON_ARRAYAGG%28CONCAT_WS%280x7a76676a636b%2Cschema_name%29%29%2C0x7176706a71%29%20FROM%20INFORMATION_SCHEMA.SCHEMATA--%20-
các câu lệnh bên trên là search.php và ?search=book , có thể là chúng đang thực hiện cuộc tấn công để lấy đi dữ liệu ,thông tin của máy chủ
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/f556133d-a376-4095-a8ec-63053364a669)
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/1df03661-274a-44b9-a1d5-d98f2c5d24a4)

Q6:

Q7:
tiếp tục khai thác thông tin từ bộ lọc http, em có thể để ý được có 2 diractory khá đáng nghi đó chính là /icons/ và /admin/
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/7aa13762-3bbb-490f-b8f0-57a8782d8a93)
và khi thử vào đáp án thì em có đáp án chính xác chnhs là /admin/


Q8:


Q9:
ngay tại diractory /admin/ em có thể thấy được một filename khá đáng ngờ chính là NVri2vhp.php
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/052fa170-2d80-4238-ad7c-67d45213e880)
và có thể đây chính là file độc hại mà kẻ tấn công đã tải lên 
và nó chính là đáp án
![image](https://github.com/Ahitriko/Training-CTF/assets/151734752/26ce0c74-dd93-4bc5-891a-1db1ae55a8ca)
