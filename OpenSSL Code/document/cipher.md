


https://zhuanlan.zhihu.com/p/37239435


https://blog.csdn.net/bytxl/article/details/48263841


openssl ��װѡ��
 no-psk    Don't build support for Pre-Shared Key based ciphersuites.
 
 
 
 /* Cipher 05 */
{
1,
SSL3_TXT_RSA_RC4_128_SHA,
SSL3_CK_RSA_RC4_128_SHA,
SSL_kRSA|SSL_aRSA|SSL_RC4 |SSL_SHA1|SSL_SSLV3,
SSL_NOT_EXP|SSL_MEDIUM,
0,
128,
128,
SSL_ALL_CIPHERS,
SSL_ALL_STRENGTHS,
}


����1��ʾ�ǺϷ��ļ����׼���
SSL3_TXT_RSA_RC4_128_SHAΪ�����׼������֣�
SSL3_CK_RSA_RC4_128_SHA Ϊ �����׼� ID ��
SSL_kRSA|SSL_aRSA|SSL_RC4 |SSL_SHA1|SSL_SSLV3 �����˸����㷨��
������Կ��������RSA�㷨��SSL_kRSA������֤����RSA�㷨��SSL_aRSA�����ԳƼ����㷨����RC4�㷨(SSL_RC4)��ժҪ����SHA1������SSLЭ������汾��
SSL_NOT_EXP|SSL_MEDIUM�����㷨��ǿ�ȡ�



����ֻ����һ�ּ����׼���
int ret=SSL_set_cipher_list(ssl,"RC4-MD5"); 
��������ֻ������һ�ּ����׼�����ô�ͻ���Ҫô����Ҫô���ش��󡣼����׼���ѡ
�����ɷ���������ġ�