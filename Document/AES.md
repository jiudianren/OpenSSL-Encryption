## AES: 高级加密标准(Advanced Encryption Standard)

[什么是AES](https://www.sohu.com/a/198681357_505794)



[AES加密算法的详细介绍与实现](https://blog.csdn.net/qq_28205153/article/details/55798628)


### 填充
### 模式
[AES五种加密模式（CBC、ECB、CTR、OCF、CFB）](https://www.cnblogs.com/starwolf/p/3365834.html)

AEC-CBC

2.密码分组链接模式（Cipher Block Chaining (CBC)）
    这种模式是先将明文切分成若干小段，然后每一小段与初始块或者上一段的密文段进行异或运算后，再与密钥进行加密。
    
    
##AES-CMAC
[C++实践（四）：C++实现AES-CMAC算法](https://blog.csdn.net/u014230646/article/details/79552843)  

AES-CMAC
 `MessageAuthentication Code（MAC）`是一种保障信息完整性和认证的密码学方法，其中CMAC的全称是Cypher-Based Message Authentication Code，基于AES等对称加密方式实现消息认证。通信双方需要共享一个对称密钥，由发送方生成一个MAC值，附在消息后面，接收方计算收到消息的MAC，如果和收到的MAC一致，则说明没有被篡改，并且能确认发送方一定拥有相同的密钥，即认证身份。

  美国国家标准与技术研究院NIST推荐了一种CMAC计算方式，可以避免CBC-MAC带来的缺点，编号为800-3B，文档可以从其官网上下载。该算法通过MAC密钥生成k1和k2两个子密钥，并规定了数据位填充的规则，可以通过AES-128、AES-192、AES-256三种模式进行MAC计算，支持所有整数字节的数据以及长度为0的输入。下图为MAC算法处理不需要位填充和需要位填充的两种情况。本文介绍AES-128生成的CMAC实现。

AES-CMAC使用了高级加密标准作为组分。为了产生一个消息认证码，CMAC需要一个密钥，消息message及消息的长度length作为输入，输出是消息认证码。

AES-CMAC的核心是CBC-MAC。对于待加密消息M，应用CBC-MAC算法。在CMAC操作中有两种情况： 
如果输入消息长度等于Block的整数倍，最后的Block M_n需要先于K1异或再进行处理； 
如果输入的消息长度不等于Block的整数倍，最后的Block M_n需要补齐到一个Block的大小，与K2异或，再进行处理。上一次处理的结果将成为下一次处理的输入。 

