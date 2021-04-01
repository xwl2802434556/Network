## Socket学习 ##
Refer:[https://www.runoob.com/python3/python3-socket.html](https://www.runoob.com/python3/python3-socket.html "python3 socket function")
### 基础客户机服务器 ###
- 服务端：
	- 导入socket模块
		`import socket`
	- 创建socket对象
		`serverSocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`
	- 设置服务器的ip地址和端口号(socket需要这两个来识别主机的服务)
		`host = socket.gethostname()
		 port = 6789`
	- 绑定端口号
		`serverSocket.bind((host, port))`
	- 设置最大连接数，超过则排队
		`serverSocket.listen(1)`
	- 死循环，一直处理客户端请求
	`while True`
		- 等待客户端连接
			`clientSocket, addr = serverSocket.accept()`
		- 处理客户端请求[发送给客户端响应]
			`print('a connection is connect\n')
			 clientSocket.send('welcome')`
		- 关闭客户端连接
			`clientSocket.close()`
	- 关闭服务端socket
		`serverSocket.close()`
- 客户端
	- 导入socket模块
		`import socket`
	- 创建socket对象
		`clientSocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)`
	- 设置服务器的ip地址和对应的端口号
		`host = socket.gethostname()
		 port = 6789`
	- 连接服务器
		`clientSocket.connect((host, port))`
	- [发送请求]
	- 接收服务器响应的1024bytes
		`msg = clientSocket.recv(1024)`
	- 关闭连接
		`clientSocket.close()`
### HTTP协议 ###
- 请求的格式
	```
	POST /index.php HTTP/1.1	请求行
	Host: localhost				请求头
	Content-Type: application/x-www-form-urlencoded
	Content-Length: 1452
	空行
	请求主体
	```
- 响应的格式
	```
	HTTP/1.1 200 OK				状态行
	Content-Type: text/html		响应头
	Content-Length: 1452
	空行
	响应主体
	```