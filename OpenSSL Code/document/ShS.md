openssl简介
https://blog.csdn.net/junkie0901/article/details/44960547

https://blog.csdn.net/w1781806162/article/details/46358747/



公有链上数据如何保护？ 

http://www.sohu.com/a/294173132_262257



	（4）       client使用到目前为止所有产生了的随机数据（shared secret），client产生本次握手中的premaster secret（这个步骤是有可能有server的参与的，由他们使用的加密算法决定），并且把这个用server的公共密钥加密，送回给server.如果server要求需要验证client，那么client也需要自己把自己的证书送过去，同时送一些自己签过名的数据过去。
	SSL协议有两种技术来产生shared secret：
	一种是RSA，一种是EDH。
	RSA就是我们上一章说过的一种不对称加密算法。首先server把自己的RSA公共密钥送给client，client于是用这个key加密一个随机产生的值（这个随机产生的值就是shared secret），再把结果送给server。
	EDH也是一种不对称加密算法，但它与RSA不同的是，它好象没有自己固定的公共密钥和私有密钥，都是在程序跑起来的时候产生的，用完就K掉。其他的步骤两者就差不多了。
	RSA、DSA、DH三种不对称加密算法的区别也就在这里。RSA的密钥固定，后两个需要一个参数来临时生成key。DH甚至要求双方使用同样的参数，这个参数要事先指定。如果SSL库没有load进这个参数，DH算法就没办法用。DSA没研究过。
	
	
	
