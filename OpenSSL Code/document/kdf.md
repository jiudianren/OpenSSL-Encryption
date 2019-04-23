密钥导出函数（Key derivation function）
https://blog.csdn.net/sjrGCkym/article/details/78195845


主要参考 文档:`NIST SP 800-108`

NIST SP 800-108密钥导出函数KDF研究 ![https://blog.csdn.net/samsho2/article/details/83592439]

openssl 消息认证码CMAC支持
https://blog.csdn.net/kkxgx/article/details/10307663



	4. Pseudorandom Function (PRF):

	伪随机函数是构建本建议书中密钥导出函数的基本构建块。通常，伪随机函数族{PRF（s，x）|s∈S}由具有索引（也称为种子）s和输入变量x的多项式时间可计算函数组成，这样当s从S中随机选择而不是观察者已知，PRF（s，x）在计算上与在相同域上定义的随机函数无法区分，其输出与PRF（s，x）的范围相同。有关伪随机函数的正式定义，请参阅[9]。
	当加密密钥KI被视为种子，即s = KI时，伪随机函数的输出可以用作密钥材料。
	
lpf: ShS作为 s，即shs就是ki . DR是X.

	
	
	
	在第5节中，定义了几个基于PRF的密钥导出函数系列，而没有描述PRF的内部结构。
	?对于密钥推导，本建议书批准使用[8]中指定的密钥哈希消息认证码（HMAC）或[7]中指定的基于密码的消息认证码（CMAC）作为伪随机函数。
	对于使用HMAC或CMAC的给定KDF，假设密钥KI在计算上与从长度为| KI |的所有二进制串的集合中随机均匀选择的密钥KI无法区分。
	注意，[1]和[2]指定了额外的（基于散列的）密钥导出函数，这些函数是根据这些文档中描述的密钥建立方案的需要而定制的

	
	5. Key Derivation Functions (KDF)
	
	
	
	
CMAC()