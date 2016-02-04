# Shell Programming

### 请问如何在shell中获得当前用户名
	name=`whoami`

### shell中if做比较


### [shell if else以及大于、小于、等于逻辑表达式](http://lxsym.blog.51cto.com/1364623/866331)


### shell截取字符串的方法
1. 使用 # 号操作符。用途是从左边开始删除第一次出现子字符串即其左边字符，保留右边字符。用法为#*substr,

	    例如：
	    str='http://www.你的域名.com/cut-string.html'
		echo ${str#*//}
		得到的结果为www.你的域名.com/cut-string.html，即删除从左边开始到第一个"//"及其左边所有字符

2. 使用 ## 号操作符。用途是从左边开始删除最后一次出现子字符串即其左边字符，保留右边字符。用法为##*substr,
    
    	例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${str##*/}
		得到的结果为cut-string.html，即删除最后出现的"/"及其左边所有字符
	
3. 使用 % 号操作符。用途是从右边开始删除第一次出现子字符串即其右边字符，保留左边字符。用法为%substr*,

		例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${str%/*}
		得到的结果为http://www.你的域名.com，即删除从右边开始到第一个"/"及其右边所有字符
		
4.  使用 %% 号操作符。用途是从右边开始删除最后一次出现子字符串即其右边字符，保留左边字符。用法为%%substr*,
		
		例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${str%%/*}
		得到的结果为http://www.你的域名.com，即删除从右边开始到最后一个"/"及其右边所有字符


5. 从左边第几个字符开始以及字符的个数，用法为:start:len,

		例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${var:0:5}
		其中的 0 表示左边第一个字符开始，5 表示字符的总个数。
		结果是：http:
		
6. 从左边第几个字符开始一直到结束，用法为:start,

		例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${var:7}
		其中的 7 表示左边第8个字符开始
		结果是：www.你的域名.com/cut-string.html
		
7. 从右边第几个字符开始以及字符的个数，用法:0-start:len,
		
		例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${str:0-15:10}
		其中的 0-6 表示右边算起第6个字符开始，10 表示字符的个数。
		结果是：cut-string
		
		
8.从右边第几个字符开始一直到结束，用法:0-start,

		例如：
		str='http://www.你的域名.com/cut-string.html'
		echo ${str:0-4}
		其中的 0-6 表示右边算起第6个字符开始，10 表示字符的个数。
		结果是：html
		注：（左边的第一个字符是用 0 表示，右边的第一个字符用 0-1 表示）



### [Linux bash shell 逐行读取文件的三种方法]("http://blog.chinaunix.net/uid-20551209-id-3761912.html")

#### 方法一，指定换行符读取：

	\#! /bin/bash  
  
	IFS="  "   
	for LINE in `cat /etc/passwd`  
	do   
        echo $LINE 
	done
	
	
#### 方法二，文件重定向给read处理：

	\#! /bin/bash  
  
	cat /etc/passwd | while read LINE  
	do
        echo $LINE 

	done
 

#### 方法三，用read读取文件重定向：

	\#! /bin/bash    
	while read LINE
	do
        echo $LINE 
	done < /etc/passwd

访问二和三比较相似，推荐用方法三