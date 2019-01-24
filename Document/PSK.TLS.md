

	
	TLS_PSK_WITH_AES_128_GCM_SHA256
	TLS_PSK_WITH_AES_128_CBC_SHA256

深度理解：TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 
https://www.topomel.com/archives/382.html


PSK在TLS中的应用
https://blog.csdn.net/mrpre/article/details/79337506

HTTPS 背后的加密算法
https://www.linuxidc.com/Linux/2015-08/121812.htm

这个过程简单来说是这样的：

浏览器把自身支持的一系列Cipher Suite（密钥算法套件，后文简称Cipher）[C1,C2,C3, …]发给服务器；
服务器接收到浏览器的所有Cipher后，与自己支持的套件作对比，如果找到双方都支持的Cipher，则告知浏览器；
浏览器与服务器使用匹配的Cipher进行后续通信。如果服务器没有找到匹配的算法，浏览器（以Firefox 30为例，后续例子中使用的浏览器均为此版本的Firefox）将给出错误信息:



PSK         pre-shared key   预先共享键 

PSK-only
简单的说，就是client写死一个key，server写死一个key，当然这两个key是一样的。
 
这个key被用来当做pms(pre master key)的一部分。当然，client 和 server也可以配置多个key，为了决定使用哪个key，每个key对应一个psk identity（字符串标识）。 
客户端会发送client key exchange，client key exchange中携带有一个字符串：identity，server收到identity，查找identity对应的key，这样就能知道客户端使用的是那个key了




A client application wishing to use PSK ciphersuites for TLSv1.2 and below must provide a different callback function. This function will be called when the client is sending the ClientKeyExchange message to the server.

The purpose of the callback function is to select the PSK identity and the pre-shared key to use during the connection setup phase.

The callback is set using functions SSL_CTX_set_psk_client_callback() or SSL_set_psk_client_callback(). The callback function is given the connection in parameter ssl, a NULL-terminated PSK identity hint sent by the server in parameter hint, a buffer identity of length max_identity_len bytes where the resulting NUL-terminated identity is to be stored, and a buffer psk of length max_psk_len bytes where the resulting pre-shared key is to be stored.

The callback for use in TLSv1.2 will also work in TLSv1.3 although it is recommended to use SSL_CTX_set_psk_use_session_callback() or SSL_set_psk_use_session_callback() for this purpose instead. If TLSv1.3 has been negotiated then OpenSSL will first check to see if a callback has been set via SSL_CTX_set_psk_use_session_callback() or SSL_set_psk_use_session_callback() and it will use that in preference. If no such callback is present then it will check to see if a callback has been set via SSL_CTX_set_psk_client_callback() or SSL_set_psk_client_callback() and use that. In this case the hint value will always be NULL and the handshake digest will default to SHA-256 for any returned PSK.

