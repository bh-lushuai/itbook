# Linux Tips

[Linux权限位（S位）](http://binyan17.iteye.com/blog/1444452)
	
	会创建s与t权限，是为了让一般用户在执行某些程序的时候，能够暂时具有该程序拥有者的权限。举例来说，我们知道，账号与密码的存放文件其实是 /etc/passwd与 /etc/shadow。而 /etc/shadow文件的权限是“-r--------”。它的拥有者是root。在这个权限中，仅有root可以“强制”存储，其他人是连看都不行的。

[Linux curl命令详解](http://www.linuxdiyf.com/linux/2800.html)

[curl cookie 抓取登陆后网页](http://blog.sina.com.cn/s/blog_63d675190100p4vg.html)

	#cookie.txt

	# Netscape HTTP Cookie File
	# http://curl.haxx.se/rfc/cookie_spec.html
	# This file was generated by libcurl! Edit at your own risk.

	netscape.com TRUE / FALSE 946684799 NETSCAPE_ID 100103
	domain - The domain that created AND that can read the variable.
	flag - A TRUE/FALSE value indicating if all machines within a given domain can access the variable. This value is set automatically by the browser, depending on the value you set for domain.
	path - The path within the domain that the variable is valid for.
	secure - A TRUE/FALSE value indicating if a secure connection with the domain is needed to access the variable.
	expiration - The UNIX time that the variable will expire on. UNIX time is defined as the number of seconds since Jan 1, 1970 00:00:00 GMT.
	name - The name of the variable.
	value - The value of the variable.

[Linux 下curl模拟Http 的get or post请求](http://blog.sina.com.cn/s/blog_6e2d53050101k230.html)

	curl -d "param1=value1&param2=value2" "http://www.baidu.com"

[linux copy cp目录强制覆盖](http://blog.sina.com.cn/s/blog_8ca23b4001019ps6.html)

	yes|cp -r /x  y
	cp -rf 即使使用了f 每个文件仍然会询问。 yes|可以解决这个问题。
