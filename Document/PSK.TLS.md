

	
	TLS_PSK_WITH_AES_128_GCM_SHA256
	TLS_PSK_WITH_AES_128_CBC_SHA256

�����⣺TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 
https://www.topomel.com/archives/382.html


PSK��TLS�е�Ӧ��
https://blog.csdn.net/mrpre/article/details/79337506

HTTPS ����ļ����㷨
https://www.linuxidc.com/Linux/2015-08/121812.htm

������̼���˵�������ģ�

�����������֧�ֵ�һϵ��Cipher Suite����Կ�㷨�׼������ļ��Cipher��[C1,C2,C3, ��]������������
���������յ������������Cipher�����Լ�֧�ֵ��׼����Աȣ�����ҵ�˫����֧�ֵ�Cipher�����֪�������
������������ʹ��ƥ���Cipher���к���ͨ�š����������û���ҵ�ƥ����㷨�����������Firefox 30Ϊ��������������ʹ�õ��������Ϊ�˰汾��Firefox��������������Ϣ:



PSK         pre-shared key   Ԥ�ȹ���� 

PSK-only
�򵥵�˵������clientд��һ��key��serverд��һ��key����Ȼ������key��һ���ġ�
 
���key����������pms(pre master key)��һ���֡���Ȼ��client �� serverҲ�������ö��key��Ϊ�˾���ʹ���ĸ�key��ÿ��key��Ӧһ��psk identity���ַ�����ʶ���� 
�ͻ��˻ᷢ��client key exchange��client key exchange��Я����һ���ַ�����identity��server�յ�identity������identity��Ӧ��key����������֪���ͻ���ʹ�õ����Ǹ�key��




A client application wishing to use PSK ciphersuites for TLSv1.2 and below must provide a different callback function. This function will be called when the client is sending the ClientKeyExchange message to the server.

The purpose of the callback function is to select the PSK identity and the pre-shared key to use during the connection setup phase.

The callback is set using functions SSL_CTX_set_psk_client_callback() or SSL_set_psk_client_callback(). The callback function is given the connection in parameter ssl, a NULL-terminated PSK identity hint sent by the server in parameter hint, a buffer identity of length max_identity_len bytes where the resulting NUL-terminated identity is to be stored, and a buffer psk of length max_psk_len bytes where the resulting pre-shared key is to be stored.

The callback for use in TLSv1.2 will also work in TLSv1.3 although it is recommended to use SSL_CTX_set_psk_use_session_callback() or SSL_set_psk_use_session_callback() for this purpose instead. If TLSv1.3 has been negotiated then OpenSSL will first check to see if a callback has been set via SSL_CTX_set_psk_use_session_callback() or SSL_set_psk_use_session_callback() and it will use that in preference. If no such callback is present then it will check to see if a callback has been set via SSL_CTX_set_psk_client_callback() or SSL_set_psk_client_callback() and use that. In this case the hint value will always be NULL and the handshake digest will default to SHA-256 for any returned PSK.

