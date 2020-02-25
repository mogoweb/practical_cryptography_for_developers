## 密钥交换和DHKE

在密码学中，[密钥建立](http://cacr.uwaterloo.ca/hac/about/chap12.pdf)(密钥交换，密钥协商)是一个过程或协议，共享密钥为双方所用，作为随后的安全用途，通常用于加密通信。建立的技术可以是密钥协商或密钥传输方案。

* 在密钥协商方案中，双方都参与共享密钥的协商。密钥协商方案的例子有Diffie-Hellman(DHKE)和Elliptic-Curve Diffie-Hellman(ECDH)。
* 在密钥传输方案中，只有一方生成共享密钥，而另一方则从其获取密钥。密钥传输方案通常是通过公钥密码学来实现的，比如在RSA密钥交换中，客户端使用其私钥对随机会话密钥进行加密，然后将其发送到服务器，在服务器中使用客户端的公钥对其进行解密。

通过设计[密钥交换](https://en.wikipedia.org/wiki/Key_exchange)方案，可以安全地在双方之间交换加密密钥，而其他任何人都无法获得密钥的副本。通常，在加密对话的开始时(例如在TLS握手阶段)，各方首先协商要在对话中使用的加密密钥(共享密钥)。密钥交换方案在现代密码学中确实是非常重要的主题，因为在Internet中，无数的设备和服务器，都要交换数百次密钥。

每当便携式计算机连接到WiFi网络或Web浏览器通过 https:// 协议打开网站时，都会进行密钥协商(密钥建立)。密钥协商可以基于匿名密钥交换协议(例如DHKE)、密码或预共享密钥(pre-shared key, PSK)、数字证书或多个方法的组合。某些通信协议仅建立一次共享密钥，而有一些则随时间不断更改密钥。

认证密钥交换(Authenticated Key Exchange, AKE)是指密钥交换协议中不仅交换会话密钥，还对有关各方的身份进行验证(例如通过密码、公钥或数字证书)。例如，如果您连接到受密码保护的WiFi网络，就会用到认证密钥协商协议，大多数是密码认证的密钥协商(password-authenticated key agreement, PAKE)。如果您连接到公共WiFi网络，则会使用匿名密钥协议。

## 密钥交换 / 密钥协商算法

现在有许多用于密钥交换和密钥建立的密码学算法。有些使用公钥密码系统，还有的使用简单的密钥交换方案(如Diffie-Hellman密钥交换)。一些涉及服务器身份验证，一些涉及客户端身份验证。有些使用密码，有些使用数字证书或其他身份验证机制。

密钥交换方案的例子有：[Diffie-Hellman密钥交换(DHКЕ)](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)和[椭圆曲线Diffie-Hellman(ECDH)](https://en.wikipedia.org/wiki/Elliptic-curve_Diffie%E2%80%93Hellman)、[RSA-OAEP](https://en.wikipedia.org/wiki/Optimal_asymmetric_encryption_padding)和[RSA-KEM](https://tools.ietf.org/html/rfc5990)(RSA密钥传输)、[PSK(预共享密钥)](https://en.wikipedia.org/wiki/Pre-shared_key)、[SRP(安全远程密码协议)](https://en.wikipedia.org/wiki/Secure_Remote_Password_protocol)，[FHMQV](https://www.cryptopp.com/wiki/Fully_Hashed_Menezes-Qu-Vanstone)(Fully Hashed Menezes-Qu-Vanstone)、[ECMQV](https://www.cryptopp.com/wiki/Elliptic_Curve_Menezes-Qu-Vanstone)(Ellictic-Curve Menezes-Qu-Vanstone)和[CECPQ1](https://en.wikipedia.org/wiki/CECPQ1)(量子安全密钥协议)。

让我们从经典的Diffie-Hellman密钥交换(DHКЕ)方案开始，它是最早的公钥协议之一。