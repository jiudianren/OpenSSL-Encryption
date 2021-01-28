
# DSA 签名的过程

https://segmentfault.com/a/1190000012158045


处理过程： （采用双重加密）
（1）使用SHA编码将发送文件加密产生128bit的数字摘要；
（2）发送方用自己的专用密钥对摘要再加密，形成数字签名；
（3）将原文和加密的摘要同时传给对方；
（4）接受方用发送方的公共密钥对摘要解密，同时对收到的文件用SHA编码加密产生同一摘要；
（5）将解密后的摘要和收到的文件在接受方重新加密产生的摘要相互对比，如果两者一致，则说明在传送过程中信息没有破坏和篡改。否则，则说明信息已经失去安全性和保密性。