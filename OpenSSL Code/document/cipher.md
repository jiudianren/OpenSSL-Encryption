


https://zhuanlan.zhihu.com/p/37239435


https://blog.csdn.net/bytxl/article/details/48263841


openssl 安装选项
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


其中1表示是合法的加密套件；
SSL3_TXT_RSA_RC4_128_SHA为加密套件的名字，
SSL3_CK_RSA_RC4_128_SHA 为 加密套件 ID ，
SSL_kRSA|SSL_aRSA|SSL_RC4 |SSL_SHA1|SSL_SSLV3 表明了各种算法，
其中密钥交换采用RSA算法（SSL_kRSA），认证采用RSA算法（SSL_aRSA），对称加密算法采用RC4算法(SSL_RC4)，摘要采用SHA1，采用SSL协议第三版本，
SSL_NOT_EXP|SSL_MEDIUM表明算法的强度。



比如只设置一种加密套件：
int ret=SSL_set_cipher_list(ssl,"RC4-MD5"); 
如果服务端只设置了一种加密套件，那么客户端要么接受要么返回错误。加密套件的选
择是由服务端做出的。