ECDH:

      ECC算法用途比RSA还猛，不仅可以加解密、签名验证。
      还可以与DH结合使用，用于密钥磋商，
      这个密钥交换算法称为ECDH。
      交换双方可以在不共享任何秘密的情况下协商出一个密钥。
      ECC是建立在基于椭圆曲线的离散对数问题上的密码体制，
      给定椭圆曲线上的一个点P，一个整数k，
      求解点Q=kP很容易；
      给定两个点P、Q，知道Q=kP，求整数k确是一个难题。
      ECDH即建立在此数学难题之上。密钥磋商过程：

      假设密钥交换双方为Alice、Bob，
      其有共享曲线参数（椭圆曲线E、阶N、基点G）。

	1)Alice生成随机整数a，计算A=a*G,
          Bob生成随机整数b，计算B=b*G。
	
	2)Alice将A传递给Bob。
          A的传递可以公开，即攻击者可以获取A。
		由于椭圆曲线的离散对数问题是难题，
		所以攻击者不可以通过A、G计算出a。
               Bob将B传递给Alice。
		同理，B的传递可以公开。
	
	3 )Bob收到Alice传递的A，计算Q=b*A
	
	4)Alice收到Bob传递的B，计算Q‘=a*B
	
	Alice、Bob双方即得
        Q=b*A=b*(a*G)
             =(b*a)*G
             =(a*b)*G
             =a*(b*G)
             =a*B=Q'(交换律和结合律)，
        即双方得到一致的密钥Q。



ECDH密钥交换的C程序
https://blog.csdn.net/yyhustim/article/details/24376867

