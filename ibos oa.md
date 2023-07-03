SQL injection vulnerability exists in ibos oa v4.5.5

official website:http://www.ibos.com.cn/

version：4.5.5

1.Log in to the background and report the packets sent by me/received by me (on the same interface)=> Captured packets in the search area。

![WPS图片(1)](https://github.com/pineapple65/cve/assets/112841820/25568f30-4f5e-419d-9296-3b5fb57f9707)

![WPS图片(2)](https://github.com/pineapple65/cve/assets/112841820/44e29a78-23ab-4c62-8fce-82f40fea0dcd)

2. Find the corresponding code through the route for analysis，Here are all the api controllers

![WPS图片(3)](https://github.com/pineapple65/cve/assets/112841820/5b631ce5-4a29-4c1c-9be9-76a5128ec5be)

Into the run() method of getlist.php,$data[keyword] assigns the incoming value to $keyword, and next passes the $keyword value to the getListCondition() method
![WPS图片(4)](https://github.com/pineapple65/cve/assets/112841820/04501c40-5c49-4f52-9f79-dcb1f0556cc6)

3.Enter the getListCondition() method and concatenate the query conditions one by one

![WPS图片(5)](https://github.com/pineapple65/cve/assets/112841820/1370d37e-dd0e-4a37-9f5e-63d925f70a7a)

![WPS图片(6)](https://github.com/pineapple65/cve/assets/112841820/5acc4369-7e29-4734-9c1b-289e62197222)

![WPS图片(7)](https://github.com/pineapple65/cve/assets/112841820/8946b372-ad2d-44eb-8f31-7c5dce716662)

4.The above concatenated sql statement is assigned to $condition and entered as an argument to the getReportByCondition() method.
![WPS图片(8)](https://github.com/pineapple65/cve/assets/112841820/87b87b51-1fef-4c34-9b86-d81a58aea82f)

Here you get the complete query statement and execute the query

![WPS图片(9)](https://github.com/pineapple65/cve/assets/112841820/9455930c-75bd-4e11-b5e4-2e06e4ada8d7)

![WPS图片(10)](https://github.com/pineapple65/cve/assets/112841820/d48b4f3a-4680-40f8-b4c3-04ec13a6df97)

5.Vulnerability recurrence
![WPS图片(11)](https://github.com/pineapple65/cve/assets/112841820/1431f4d8-363e-4c51-81f7-c2fa9faa07b3)

