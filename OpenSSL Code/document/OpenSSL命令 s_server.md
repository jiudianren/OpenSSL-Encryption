	openssl s_server 
	-cert server.pem 
	-key server.key 
	-tls1_2 
	-psk 1a2b3c4d 
	-port 9999 
	-cipher PSK-AES128-CBC-SHA256
	
	
	
	openssl s_client -psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 -tls1_2 -psk 1a2b3c4d  -connect 127.0.0.1:20590 -cipher PSK-AES128-CBC-SHA256
	
	./openssl s_client -psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 -tls1_2 -psk 1a2b3c4d  -connect 10.45.19.229:20590 -cipher PSK-AES128-CBC-SHA256
	
	openssl s_client 
	-psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 	-tls1_2 
	-psk 1a2b3c4d  
	-connect 127.0.0.1:20590 
	-cipher PSK-AES128-CBC-SHA256
	openssl s_client 
	-psk_identity 8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140 
	-tls1_2 
	-psk 1a2b3c4d  
	-connect 127.0.0.1:20590 
	-cipher PSK-AES128-CBC-SHA256
	



openssl-1.1.0c ciphers -V 'PSK' 


openssl s_server 
-cert server.pem   	ʹ�õ�֤���ļ�����������������㷨�׼���Ҫһ��֤�飬
					����һЩ��Ҫ֤��Ĺ�Կ���ͣ�����DSS�㷨�����Ҫ֤�飨����һ��DSS��DSA����Կ����ȱʡʹ�� ./server.pem��

-key server.key   ʹ�õ�˽����Կ�ļ������û��ָ������ô֤���ļ��ᱻʹ�ã�ʹ�õ���֤�鹫Կֵ����
-tls1_2    -ssl2��-ssl3��-tls1_1��-tls1_2��-tls1��-dtls1��-no_ssl2��-no_ssl3��-no_tls1��-no_tls1_1��-no_tls1_2��ʹ�õ�Э��״ֵ̬    


-psk 1a2b3c4d     PSK in hex (without 0x)
-port 9999      �����˿�
-cipher PSK-AES128-CBC-SHA256





openssl s_client 
-psk_identity 
8001028110890010120123412340123456789012244F10000102030405060708090A0B0C0D0E0F820101830140

-psk_identity val          PSK identity
 -psk val                   PSK in hex (without 0x) 
-tls1_2 
-psk 1a2b3c4d  
-connect 127.0.0.1:20590 
-cipher PSK-AES128-CBC-SHA256
