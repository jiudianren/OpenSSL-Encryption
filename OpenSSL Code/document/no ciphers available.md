
	1 OpenSSL安装说明
	安装过程比较简单，更详细的安装说明可以参考安装包中根目录下的文件“INSTALL”，安装说明如下：
	1．解压安装包：gunzip -c openssl- 1.0.1e.tar.gz |tar xfv -
	2．进入解压后的目录：cd openssl- 1.0.1e 
					./config shared --debug  --prefix=/home/aaav81/tools/runtime
	3．配置安装路径：./config  --debug  --prefix=/home/aaav81/tools/runtime
	4．执行编译：make&& make install
	目前AAA的PEAP认证需要建立TLS安全连接，所以openssl是编译AAA的必备库，请提前安装

/home/pcrf/openssl_lpf/openssl


./config  --debug  --prefix=/home/pcrf/openssl_lpf/openssl  --openssldir=/home/pcrf/openssl_lpf/openssldir 

openssldir
--prefix=/opt/openssl --openssldir=/usr/local/ssl

https://blog.csdn.net/kelsel/article/details/52758432


 size_t SSL_client_hello_get0_ciphers(SSL *s, const unsigned char **out);
 

-cipher cipherlist：由我们自己来决定选用什么加密算法，尽管是由server来决定使用什么算法列表，但它一般都会采用我们送过去的cipher列表里的第一个cipher。

https://curl.haxx.se/docs/ssl-ciphers.html

WolfSSL WinSSL



	openssl s_server 
	-cert server.pem 
	-key server.key 
	-tls1_2 
	-psk 1a2b3c4d 
	-port 9999 
	-cipher PSK-AES128-CBC-SHA256
	
	
	
	openssl s_client -psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 -tls1_2 -psk 1a2b3c4d  -connect 127.0.0.1:20590 -cipher PSK-AES128-CBC-SHA256
	
	openssl s_client -psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 -tls1_2 -psk 1a2b3c4d  -connect 10.45.19.229:20590 -cipher PSK-AES128-CBC-SHA256
	

	set args s_client -psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 -tls1_2 -psk 1a2b3c4d  -connect 10.45.19.229:20590 -cipher PSK-AES128-CBC-SHA256
	b ssl_cipher_list_to_bytes
	b SSL_CTX_set_cipher_list
	b SSL_renegotiate
	b tls_construct_client_hello
	b psk_use_session_cb
	b tls_setup_handshake
	b psk_client_cb
	
	b ssl_set_client_disabled
	
	b SSL_CTX_set_psk_client_callback

有用：
https://blog.csdn.net/Trustauth/article/details/78130674


 openssl ciphers -s -v  PSK-AES128-GCM-SHA256:PSK-AES128-CBC-SHA256


在消息传输过程中采用对称加密(比公钥加密在速度上有极大的提高),其所用秘钥(shared secret)在握手过程中中协商(每次对话过程均不同, 在一次对话中都有可能有几次改变),并通过公钥加密的手段由客户端提交服务端.


在客户端和服务器端建立安全连接之前，双方都必须指定适合自己的加密套件。加密套件的选择可以通过组合的字符串来控制。
字符串的形式举例：ALL:!ADH:RC4+RSA:+SSLv2:@STRENGTH。
Openssl定义了4中选择符号：“＋”，“－”，“！”，“@”。其中，“＋”表示取交集；“－”表示临时删除一个算法；“！”表示永久删除一个算法；“@“表示了排序方法。
多个描述之间可以用“：”、“，”、“ ”、“；”来分开。选择加密套件的时候按照从左到的
顺序构成双向链表，存放与内存中。
--------------------- 
作者：kelsel 
来源：CSDN 
原文：https://blog.csdn.net/kelsel/article/details/52758432 
版权声明：本文为博主原创文章，转载请附上博文链接！



https://www.cnblogs.com/LiuYanYGZ/p/6004990.html



查看 cipher 相关函数

https://www.openssl.org/docs/manmaster/man3/SSL_CTX_get_ciphers.html

SSL_get_ciphers() returns the stack of available SSL_CIPHERs for ssl, sorted by preference. If ssl is NULL or no ciphers are available, NULL is returned.

SSL_CTX_get_ciphers() returns the stack of available SSL_CIPHERs for ctx.

SSL_get1_supported_ciphers() returns the stack of enabled SSL_CIPHERs for ssl as would be sent in a ClientHello (that is, sorted by preference). The list depends on settings like the cipher list, the supported protocol versions, the security level, and the enabled signature algorithms. SRP and PSK ciphers are only enabled if the appropriate callbacks or settings have been applied. The list of ciphers that would be sent in a ClientHello can differ from the list of ciphers that would be acceptable when acting as a server. For example, additional ciphers may be usable by a server if there is a gap in the list of supported protocols, and some ciphers may not be usable by a server if there is not a suitable certificate configured. If ssl is NULL or no ciphers are available, NULL is returned.

SSL_get_client_ciphers() returns the stack of available SSL_CIPHERs matching the list received from the client on ssl. If ssl is NULL, no ciphers are available, or ssl is not operating in server mode, NULL is returned.
