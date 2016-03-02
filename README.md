>commons-fileupload-1.2.1.jar
commons-io-1.3.2.jar
必须用到两个库文件

##文件上传

为了获取一些上传文件的信息，如文件名、文件类型，需要按照一定的规则在Action中增加一些getter和setter方法。

上传文件时，可以对文件的大小、文件类型等进行控制。

Struts2提供的文件拦截器，常用属性：
	maximumSize 设置文件上传的最大长度（以字节为单位），默认为2MB。
	allowedTypes  设置上传文件的类型，以“,”为分隔符，可以上传多种类型的文件，如text/html，
				      如果不设置该属性就是允许任何类型的文件。
	如果使用了拦截器对上传文件进行过滤，一旦上传的文件格式不符合要求，将在页面中提示异常信息，
	提示的异常信息是Struts2框架中格式为“键=值”的信息，常用的“键”如下：
	1.struts.messages.error.content.type.not.allowed 设置上传文件类型不匹配的提示信息
	2.struts.messages.error.file.too.large 设置上传文件太大时的提示信息
	3.struts.messages.error.uploading 设置文件不能上传时的通用提示信息
	这些可以在国际化资源文件中设置。
	
java文件
l 类型为File的xxx属性：用来封装页面文件域对应的文件内容。
l 类型为String的xxxFileName属性：用来封装该文件域对应的文件的文件名。
l 类型为String的xxxContentType属性：用来封装该文件域应用的文件的文件类型。

##文件下载
	需要在struts.xml配置用于下载的拦截<result name="success" type="stream">
	stream常用参数值如下：
	contentType 文件类型 常有text/xml text/gif text/plain纯文本 
	inputName 输入流入口.如果 在Action声明getInputStream()方法，在struts.xml配置<param name="inputName">inputStream</param>
					  如果 在Action声明getTargetFile()方法，在struts.xml配置<param name="inputName">targetFile</param>
	contentDisposition 指定下载方式（内联Inline或附件Attachment）
	bufferSize 缓存大小
	还可设置未登录不让下载
