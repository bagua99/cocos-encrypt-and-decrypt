# cocos-encrypt-and-decrypt
cocos xxxtea
解密：

1、首先将闲来广东麻将guangdongmj.apk改名后缀闲来广东麻将guangdongmj.rar

2、解压出闲来广东麻将guangdongmj.rar拷贝assets\src_et目录源代码到input目录

3、编辑decrypt.bat,设置签名和密钥 (xxxteaTool.exe input output SQLLiteData mXjv7U5dUl1aMTVV_xianlai 0 .plist;.wav;.mp3;)

   input是载入目录,output输出目录,SQLLiteData签名,mXjv7U5dUl1aMTVV_xianlai密钥,0解密,.plist;.wav;.mp3;过滤文件


加密：

1、首先将闲来广东麻将guangdongmj.apk改名后缀闲来广东麻将guangdongmj.rar
2、解压出闲来广东麻将guangdongmj.rar拷贝assets\src_et目录源代码到input目录
3、编辑encrypt.bat,设置签名和密钥 (xxxteaTool.exe input output SQLLiteData mXjv7U5dUl1aMTVV_xianlai 1 .plist;.wav;.mp3;)
   input是载入目录,output输出目录,SQLLiteData签名,mXjv7U5dUl1aMTVV_xianlai密钥,1解密,.plist;.wav;.mp3;过滤文件



加密解密不限lua文件,使用所有xxxtea加密算法



签名查找方法：

1、用记事本打开2~3个加密文件，对比找出前面相同文本，即为签名

密钥查找方法：

1、用IDA打开lib\armeabi目录下libcocos2dlua.so查找applicationDidFinishLaunching函数即可看到SQLLiteData附近的mXjv7U5dUl1aMTVV_xianlai

2、用IDA打开lib\armeabi目录下libcocos2dlua.so按ALT+T查找字符串SQLLiteData附近即可看到mXjv7U5dUl1aMTVV_xianlai



此分享用来破解cocos源码和图片等资源用于学习，请勿用于其他使用
