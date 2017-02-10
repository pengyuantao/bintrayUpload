## **1.在project的build.gradle中dependencies节点添加：**

	classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1' //生成Maven所需文件

	classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.6' //上传Maven生成的文件到Bintray

## **2.在projcet的local.properties添加：**
	#配置bintray账号相关信息
	#bintray用户名,不是登陆邮箱,是个人中心右上角显示的名字
	bintray.user=xxxxx
	#bintray的ApiKey
	bintray.apiKey=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
	#bintray的Organization Id
	bintray.organizationId=xxxxxxxx
	#配置开发者信息
	#昵称
	developer.id=xxxxxxxxxxxx
	#姓名
	developer.name=xxxxxxxxxxxxxxx
	#邮箱
	developer.email=xxxxxxxxxxxxxxx@126.com

## **3.在需要上传的model中创建project.properties文件,并添加以下内容：**
	#project
	#仓库名称，就是在bintray官网建立的仓库的名称
	project.repositoryName=maven
	#项目名称
	project.name=xxxxxxx
	#项目组id
	project.groupId=xx.xx.xxx
	#项目id,一般同project.name
	project.artifactId=xxxxx
	#打包类型
	project.packaging=aar
	#项目官方网站地址(可以随便写)
	project.siteUrl=https://github.com/xxxxx/xxxx.git
	#项目git地址(可以随便写)
	project.gitUrl=https://github.com/xxxxx/xxxx.git
	#生成的javadoc名称
	javadoc.name=xxxx

## **4.在需要上传的model的build.gradle的最下面添加：**
 	apply from: "https://raw.githubusercontent.com/pengyuantao/bintrayUpload/master/bintrayUpload.gradle"

## **5.在Terminal中运行以下命令： **
 	gradlew install
 	gradlew bintrayUpload
    
## 常见问题：
  1. javadoc失败，查看Terminal中编译产生的错误，修改注释，然后重新编译。
  2. java.lang.UnsupportedClassVersionError: com/android/build/gradle/AppPlugin : Unsupported major.minor version 52.0 修改AndroidStudio2.2的java环境为java8
  3.如果库文件有版本更新，需要修改model中的versionName的值。
