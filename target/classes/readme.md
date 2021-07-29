首先在命令行输入命令，将jar导入maven：
mvn install:install-file   -Dfile=D:\Desktop\Project\斑马打印机\zebraPrint\src\main\resources\QRCode.jar -DgroupId=cn.zebra  -DartifactId=QRCode -Dversion=1.3.0 -Dpackaging=jar

pom.xml
```xml
 <dependencies>
        <dependency>
            <groupId>cn.zebra</groupId>
            <artifactId>QRCode</artifactId>
            <version>1.3.0</version>
        </dependency>
    </dependencies>
```

第一种方案：直接使用zpl指令打印
需要点阵字库的支持 ts24.lib
如果要打印二维码还需要QRCode.jar
缺点：无法更改字体样式，只能修改字体倍率

注：关于二维码（一般采用BQ格式），如果二维码中不包含汉字则可以直接使用BQ指令 ^BQa,b,c,d,e
如果有汉字，则首先使用QRCode.jar生成png图片或者直接生成图像缓存BufferedImage，然后把图片转换成十六进制字符串，使用DG和XG指令打印(DG和XG后的名字一定要一致)



第二种方案：先把整个标签做成图片，然后把整个图片转换成十六进制字符串生成整个图片的zpl指令进行打印，也是使用DG和XG指令
如果需要生成二维码则需要QRCode.jar，否则不需要引入任何第三方的库
第二种方法可以随意更改字体、字号及样式

有关zpl指令的问题请参考  ZPL语言中文手册_ZHCN.pdf
