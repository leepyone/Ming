# JavaWeb

## 1、简介

记录Javaweb的一些不太熟悉的知识点

## 2、表单 

### 1、form标签



```html
<form action="demo_form.php" method="get">
  First name: <input type="text" name="fname"><br>
  Last name: <input type="text" name="lname"><br>
  <input type="submit" value="提交">
</form>
```

属性：

action：规定当提交表单时向何处发送表单数据。

method：规定用于发送表单数据的 HTTP 方法

### 2、input标签

<input> 标签规定了用户可以在其中输入数据的输入字段。

<input> 元素在 <form> 元素中使用，用来声明允许用户输入数据的 input 控件

```html
<input type="text" name="fname">

<form>
  <input type="text" value="hhh"> #value表示显示在文本框中的值，用户输入的时候需要删除
  <input type="password" placeholder="密码" maxlength="4"> #placeholder作用为提示，文本框中呈灰色字体，输入的时候自动消失，maxlength表示最大能输入的字符（即只能输入4个字符的密码）
  <input type="text" size="30"> # size会生成一个可见30个字符大小的文本框
  <input type="text" value="hhh" readonly> # readonly是没有值的属性，表示只读，无法修改输入。
</form>
 <form>
    <input type="email">     #定义用于 e-mail 地址的文本字段
    <input type="color"><br> #定义拾色器
    <input type="time"><br>  #定义时、分、秒（带有 time 控件）  
    <input type="week"><br>  #定义周（带有 calendar 控件）
    <input type="month"><br> #定义月（带有 calendar 控件）
    <input type="date"><br>  #定义日期（带有 calendar 控件）
    <input type="datetime-local">  #定义日期及时间（带有 calendar 和 time 控件）
  </form>
```

属性：

type：

1、text：定义**单行**输入字段 不可换行

2、password：定义密码字段，字段中的字符会被遮蔽

3、button：定义可点击的按钮（大多与 JavaScript 使用来启动脚本）

4、submit：定义提交按钮，向服务器发送数据，根据form标签中的action地址提交

5、hidden：隐藏输入字段，但是提交表单会一起被提交上去

6、image：定义图像作为提交按钮

7、file：提供供文件上传

### 3、button标签

```html
<form action="demo_form.html" method="get">
  First name: <input type="text" name="fname"><br>
  Last name: <input type="text" name="lname"><br>
  <button type="submit" value="提交">提交</button>
  <button type="reset" value="重置">重置</button>
</form>
```

属性：

type：

1、submit：提交表单信息

2、reset：重置表单信息

3、button：该按钮是可点击的按钮

### 4、textarea标签

定义了一个多行输入的区域

### 5、select标签

创建下拉列表

```html
<select name="select1">
    <option value="volvo">Volvo</option>
    <option value="saab">Saab</option>
    <option value="mercedes">Mercedes</option>
    <option value="audi">Audi</option>
</select>
```

属性：

**name**：表单提交的变量名

## 3、HTTP请求方法

### **1、HTTP协议**

超文本传输协议（HTTP）的设计目的是保证客户机与服务器之间的通信。

HTTP 的工作方式是客户机与服务器之间的**请求-应答协议**。

web 浏览器可能是客户端，而计算机上的网络应用程序也可能作为服务器端。

举例：客户端（浏览器）向服务器提交 HTTP 请求；服务器向客户端返回响应。响应包含关于请求的状态信息以及可能被请求的内容。

### **2、两种最常被用到的方法是：GET 和 POST。**

### **3、GET方法**

使用GET方法提交的参数信息会显示再url之中，相较而言不安全

```Java
/test/demo_form.asp?name1=value1&name2=value2
```

- GET 请求可被缓存
- GET 请求保留在浏览器历史记录中
- GET 请求可被收藏为书签
- GET 请求不应在处理敏感数据时使用
- GET 请求有长度限制
- GET 请求只应当用于取回数据

### 4、POST方法

查询字符串（名称/值对）是在 POST 请求的 HTTP 消息主体中发送的，请求信息没有放在url中

```
POST /test/demo_form.asp HTTP/1.1
Host: w3schools.com
name1=value1&name2=value2
```

- POST 请求不会被缓存

- POST 请求不会保留在浏览器历史记录中

- POST 不能被收藏为书签

- POST 请求对数据长度没有要求

### 5、GET与POST对比

|                  | GET                                                          | POST                                                         |
| :--------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 后退按钮/刷新    | 无害                                                         | 数据会被**重新提交**（浏览器应该告知用户数据会被重新提交）。 |
| 书签             | 可收藏为书签                                                 | 不可收藏为书签                                               |
| 缓存             | 能被缓存                                                     | 不能缓存                                                     |
| 编码类型         | application/x-www-form-urlencoded                            | application/x-www-form-urlencoded 或 multipart/form-data。为二进制数据使用多重编码。 |
| 历史             | 参数保留在浏览器历史中。                                     | 参数不会保存在浏览器历史中。                                 |
| 对数据长度的限制 | 是的。当发送数据时，GET 方法向 URL 添加数据；URL 的长度是受限制的（URL 的最大长度是 2048 个字符）。 | 无限制。                                                     |
| 对数据类型的限制 | 只允许 ASCII 字符。                                          | 没有限制。也允许二进制数据。                                 |
| 安全性           | 与 POST 相比，GET 的安全性较差，因为所发送的数据是 URL 的一部分。在发送密码或其他敏感信息时绝不要使用 GET ！ | POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中。 |
| 可见性           | 数据在 URL 中对所有人都是可见的。                            | 数据不会显示在 URL 中。                                      |

### 6、其他的HTTP请求方法

| 方法       | 描述                                              |
| :--------- | :------------------------------------------------ |
| HEAD       | 与 GET 相同，但只返回 HTTP 报头，不返回文档主体。 |
| **PUT**    | 上传指定的 URI 表示。                             |
| **DELETE** | 删除指定资源。                                    |
| OPTIONS    | 返回服务器支持的 HTTP 方法。                      |
| CONNECT    | 把请求连接转换到透明的 TCP/IP 通道。              |

## 4、RESTful风格

参考地址：https://www.runoob.com/w3cnote/restful-architecture.html

明天再看



### 1、简介

REST全称是Representational State Transfer，中文意思是表述（编者注：通常译为表征）性状态转移。

- 资源与URI
- 统一资源接口
- 资源的表述
- 资源的链接
- 状态的转移

### 2、url与uri

**URI—Uniform Resource Identifier通用

资源标志符**
Web上可用的每种资源如HTML文档、图像、视频片段、程序等都是一个来URI来定位的
URI一般由三部组成
①访问资源的命名机制
②存放资源的主机名
③资源自身的名称，由路径表示，着重强调于资源。



**URL—Uniform Resource Location统一资源定位符**
URL是Internet上用来描述信息资源的字符串，主要用在各种WWW客户程序和服务器程序上，特别是著名的Mosaic。
采用URL可以用一种统一的格式来描述各种信息资源，包括文件、服务器的地址和目录等。
URL一般由三部组成
①协议(或称为服务方式)
②存有该资源的主机IP地址(有时也包括端口号)
③主机资源的具体地址。如目录和文件名等



**URI**是一个用于标识互联网资源名称的字符串，就是一个资源的id

**URl**：就是uri的一种形式，再互联网中的一种实现，定位符，也就是说可以在通过url找到这个资源

### 3、统一资源接口

RESTful架构应该遵循统一接口原则，统一接口包含了一组受限的预定义的操作，不论什么样的资源，都是通过使用相同的接口进行资源的访问。接口应该使用标准的HTTP方法如GET，PUT和POST，并遵循这些方法的语义。

下面列出了GET，DELETE，PUT和POST的典型用法:

#### GET

- 安全且幂等
- 获取表示
- 变更时获取表示（缓存）

- 200（OK） - 表示已在响应中发出

- 204（无内容） - 资源有空表示
- 301（Moved Permanently） - 资源的URI已被更新
- 303（See Other） - 其他（如，负载均衡）
- 304（not modified）- 资源未更改（缓存）
- 400 （bad request）- 指代坏请求（如，参数错误）
- **404 （not found）- 资源不存在**
- 406 （not acceptable）- 服务端不支持所需表示
- 500 （internal server error）- 通用错误响应
- 503 （Service Unavailable）- 服务端当前无法处理请求

#### POST

- 不安全且不幂等
- 使用服务端管理的（自动产生）的实例号创建资源
- 创建子资源
- 部分更新资源
- 如果没有被修改，则不过更新资源（乐观锁）

- 200（OK）- 如果现有资源已被更改

- 201（created）- 如果新资源被创建
- 202（accepted）- 已接受处理请求但尚未完成（异步处理）
- 301（Moved Permanently）- 资源的URI被更新
- 303（See Other）- 其他（如，负载均衡）
- 400（bad request）- 指代坏请求
- 404 （not found）- 资源不存在
- 406 （not acceptable）- 服务端不支持所需表示
- 409 （conflict）- 通用冲突
- 412 （Precondition Failed）- 前置条件失败（如执行条件更新时的冲突）
- 415 （unsupported media type）- 接受到的表示不受支持
- 500 （internal server error）- 通用错误响应
- 503 （Service Unavailable）- 服务当前无法处理请求

#### PUT

- 不安全但幂等
- **用客户端管理的实例号创建一个资源**
- 通过替换的方式更新资源
- 如果未被修改，则更新资源（乐观锁）

- 200 （OK）- 如果已存在资源被更改

- 201 （created）- 如果新资源被创建
- 301（Moved Permanently）- 资源的URI已更改
- 303 （See Other）- 其他（如，负载均衡）
- 400 （bad request）- 指代坏请求
- 404 （not found）- 资源不存在
- 406 （not acceptable）- 服务端不支持所需表示
- 409 （conflict）- 通用冲突
- 412 （Precondition Failed）- 前置条件失败（如执行条件更新时的冲突）
- 415 （unsupported media type）- 接受到的表示不受支持
- 500 （internal server error）- 通用错误响应
- 503 （Service Unavailable）- 服务当前无法处理请求

#### DELETE

- 不安全但幂等
- 删除资源

- 200 （OK）- 资源已被删除

- 301 （Moved Permanently）- 资源的URI已更改
- 303 （See Other）- 其他，如负载均衡
- 400 （bad request）- 指代坏请求
- 404 （not found）- 资源不存在
- 409 （conflict）- 通用冲突
- 500 （internal server error）- 通用错误响应
- 503 （Service Unavailable）- 服务端当前无法处理请求





HTTP的请求方法与CRUD动作的匹配

- Create：POST
- Read: GET
- Update: PUT 或 PATCH
- Delete： DELETE

**未完待添加 2020/1/30**

## 5、javaweb中的页面跳转

### 1、重定向与转发

**forward（转发）**：

是服务器请求资源,服务器直接访问目标地址的URL,把那个URL的响应内容读取过来,然后把这些内容再发给浏览器.浏览器根本不知道服务器发送的内容从哪里来的,因为这个跳转过程实在服务器实现的，并不是在客户端实现的所以客户端并不知道这个跳转动作，所以它的**地址栏还是原来的地址**.

**redirect（重定向）**：

是服务端根据逻辑,发送一个状态码,告诉浏览器重新去请求那个地址.所以**地址栏显示的是新的URL**.

**转发是服务器行为，重定向是客户端行为。**



**区别**

1、地址栏的url的是否改变

2、请求的次数 redirect 有两次请求 ，而forward只有依次

3、从运用地方来说
forward:一般用于用户登陆的时候,根据角色转发到相应的模块.
redirect:一般用于用户注销登陆时返回主页面和跳转到其它的网站等

## 6、Session

