# Readytogo

## 使用keytool工具生成数字证书
`
cd %HOMEPATH%\.gradle
keytool -genkey -alias demo.keystore -keyalg RSA -validity 40000 -keystore demo.keystore
`
- keytool是工具名称，-genkey意味着执行的是生成数字证书操作，-v表示将生成证书的详细信息打印出来，显示在dos窗口中
- -alias demo.keystore表示证书的别名为“ demo.keystore”，当然可以不和上面的文件名一样
- -keyalg RSA 表示生成密钥文件所采用的算法为RSA；
- -validity 40000 表示该数字证书的有效期为40000天，意味着20000天之后该证书将失效
- -keystore demo.keystore  表示生成的数字证书的文件名为“demo.keystore”

## 配置gradle
`
cd %HOMEPATH%\.gradle
vim gradle.properties

RELEASE_STORE_FILE=%HOMEPATH%/.gradle/demo.keystore
RELEASE_KEY_ALIAS=demo.keystore
RELEASE_KEY_PASSWORD=123456
RELEASE_STORE_PASSWORD=123456
`

## 配置firebase
打开app/build.gradle，获取 applicationId "com.xxx.yyy"
打开https://console.firebase.google.com，创建项目
添加Android应用，填入包名"com.xxx.yyy"，注册应用
下载google-services.json，将该文件放在你应用的build.gradle同级目录中，添加Firebase SDK


