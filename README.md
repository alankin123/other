# Android Studio导入Eclipse工程的步骤 #
1.原有的Eclipse工程项目文件结构是这样的。如果要迁移后的项目兼容Eclipse，那只能删除gen文件夹。如果迁移后不再有在Eclipse中编辑的需求，可以继续删除.classpath,.project文件。 

<div align=center>
<img src="http://i.imgur.com/KUNyTYG.png" />
</div>

2.在项目的build.gradle中的android{}中导入以下代码用于AS识别Eclipse的项目结构: 
   
    sourceSets {
    main {
    manifest.srcFile 'AndroidManifest.xml'
    java.srcDirs = ['src']
    aidl.srcDirs = ['src']
    renderscript.srcDirs = ['src']
    res.srcDirs = ['res']
    assets.srcDirs = ['assets']
    jniLibs.srcDirs = ['libs']
    }
    instrumentTest.setRoot('tests')
    }  
3.把settings.gradle的include ':app' 删除,添加上改module的名字，切记module中一定不要有'-'，因为有些从github上面下载下来的项目带有-master，gradle里面是识别不了'-'的。
