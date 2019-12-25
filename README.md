# Android-

很久没有回到自己的github 了，每天都是赶项目赶项目，扎心了这两年，在开发中的一点点，我想都可以记录下来，现在记录Android 自动打包并且上传到fir 的小功能


在项目的build 目录下，记得是app 的build ，不是root 的build啧，新建一个方法，用来全局调用，等下会解释


因为在这里写上代码，会错乱，所以大家下载UploadFir 方法，

在项目的build 里面的android 里面增加以下方法

    /**
     * 自动打包debug 版本并上传到Fir
     */
    task uploadDebugToFir() {
        dependsOn 'assembleDebug'
        group 'upLoadApkToFir'  //设置分组，在Gradle中，显示一个名称为upLoadApkToFir的任务组
        doLast {
            upLoadFun(defaultConfig,"assembleDebug")
        }
    }

    /**
     * 自动打包Release 版本并上传到Fir
     */
    task uploadReleaseToFir() {
        dependsOn 'assembleRelease'
        group 'upLoadApkToFir'  //设置分组，在Gradle中，显示一个名称为upLoadApkToFir的任务组
        doLast {
            upLoadFun(defaultConfig,"assembleRelease")
        }
    }


在Android studio 里面Terminal 控制台执行命令就可以了

gradlew uploadReleaseToFir

gradlew uploadDebugToFir


