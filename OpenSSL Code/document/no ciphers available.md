
	1 OpenSSL��װ˵��
	��װ���̱Ƚϼ򵥣�����ϸ�İ�װ˵�����Բο���װ���и�Ŀ¼�µ��ļ���INSTALL������װ˵�����£�
	1����ѹ��װ����gunzip -c openssl- 1.0.1e.tar.gz |tar xfv -
	2�������ѹ���Ŀ¼��cd openssl- 1.0.1e 
					./config shared --debug  --prefix=/home/aaav81/tools/runtime
	3�����ð�װ·����./config  --debug  --prefix=/home/aaav81/tools/runtime
	4��ִ�б��룺make&& make install
	ĿǰAAA��PEAP��֤��Ҫ����TLS��ȫ���ӣ�����openssl�Ǳ���AAA�ıر��⣬����ǰ��װ

/home/pcrf/openssl_lpf/openssl


./config  --debug  --prefix=/home/pcrf/openssl_lpf/openssl  --openssldir=/home/pcrf/openssl_lpf/openssldir 

openssldir
--prefix=/opt/openssl --openssldir=/usr/local/ssl

https://blog.csdn.net/kelsel/article/details/52758432


 size_t SSL_client_hello_get0_ciphers(SSL *s, const unsigned char **out);
 

-cipher cipherlist���������Լ�������ѡ��ʲô�����㷨����������server������ʹ��ʲô�㷨�б�����һ�㶼����������͹�ȥ��cipher�б���ĵ�һ��cipher��

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

���ã�
https://blog.csdn.net/Trustauth/article/details/78130674


 openssl ciphers -s -v  PSK-AES128-GCM-SHA256:PSK-AES128-CBC-SHA256


����Ϣ��������в��öԳƼ���(�ȹ�Կ�������ٶ����м�������),��������Կ(shared secret)�����ֹ�������Э��(ÿ�ζԻ����̾���ͬ, ��һ�ζԻ��ж��п����м��θı�),��ͨ����Կ���ܵ��ֶ��ɿͻ����ύ�����.


�ڿͻ��˺ͷ������˽�����ȫ����֮ǰ��˫��������ָ���ʺ��Լ��ļ����׼��������׼���ѡ�����ͨ����ϵ��ַ��������ơ�
�ַ�������ʽ������ALL:!ADH:RC4+RSA:+SSLv2:@STRENGTH��
Openssl������4��ѡ����ţ���������������������������@�������У���������ʾȡ��������������ʾ��ʱɾ��һ���㷨����������ʾ����ɾ��һ���㷨����@����ʾ�����򷽷���
�������֮������á����������������� �������������ֿ���ѡ������׼���ʱ���մ��󵽵�
˳�򹹳�˫������������ڴ��С�
--------------------- 
���ߣ�kelsel 
��Դ��CSDN 
ԭ�ģ�https://blog.csdn.net/kelsel/article/details/52758432 
��Ȩ����������Ϊ����ԭ�����£�ת���븽�ϲ������ӣ�



https://www.cnblogs.com/LiuYanYGZ/p/6004990.html



�鿴 cipher ��غ���

https://www.openssl.org/docs/manmaster/man3/SSL_CTX_get_ciphers.html

SSL_get_ciphers() returns the stack of available SSL_CIPHERs for ssl, sorted by preference. If ssl is NULL or no ciphers are available, NULL is returned.

SSL_CTX_get_ciphers() returns the stack of available SSL_CIPHERs for ctx.

SSL_get1_supported_ciphers() returns the stack of enabled SSL_CIPHERs for ssl as would be sent in a ClientHello (that is, sorted by preference). The list depends on settings like the cipher list, the supported protocol versions, the security level, and the enabled signature algorithms. SRP and PSK ciphers are only enabled if the appropriate callbacks or settings have been applied. The list of ciphers that would be sent in a ClientHello can differ from the list of ciphers that would be acceptable when acting as a server. For example, additional ciphers may be usable by a server if there is a gap in the list of supported protocols, and some ciphers may not be usable by a server if there is not a suitable certificate configured. If ssl is NULL or no ciphers are available, NULL is returned.

SSL_get_client_ciphers() returns the stack of available SSL_CIPHERs matching the list received from the client on ssl. If ssl is NULL, no ciphers are available, or ssl is not operating in server mode, NULL is returned.
