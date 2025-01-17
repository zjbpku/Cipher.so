<p align="center"><a href="https://github.com/MEiDIK/Cipher.so" target="_blank"><img width="200"src="logo.png"></a></p>
<h1 align="center">Cipher.so</h1>
<p align="center">Providing a simple way to keep your secure info safe for android app development.</p>
<p align="center">
  <a href='https://bintray.com/idik-net/Cipher.so/cipher.so/_latestVersion'><img src='https://api.bintray.com/packages/idik-net/Cipher.so/cipher.so/images/download.svg'></a>
  <a href="https://github.com/MEiDIK/Cipher.so/blob/master/LICENSE"><img src="https://img.shields.io/github/license/MEiDIK/Cipher.so.svg" alt="GitHub license"></a>
  <a href="http://androidweekly.net/issues/issue-288"><img src="https://img.shields.io/badge/Android%20Weekly-%23288-green.svg" alt="Android Weekly"></a>
  <a href="#"><img src="https://img.shields.io/badge/Recommend-%E2%AD%90%EF%B8%8F%E2%AD%90%EF%B8%8F%E2%AD%90%EF%B8%8F%E2%AD%90%EF%B8%8F%E2%AD%90%EF%B8%8F-green.svg" alt="Recommend"></a>
</p>

## Wiki

  * [中文](https://github.com/MEiDIK/Cipher.so#%E5%85%B3%E4%BA%8E)

  * [English](https://github.com/MEiDIK/Cipher.so#about)

-----

## About

### How it works?

All the key-values will be auto package into a native library during the compile time. Then your can obtain them from the Java interface generated by Cipher.so.

### Features

* Encrypt secure info in a native library via easy configs
* Reflection free

---
## Usages

#### Installation
##### Step 1. in the root build.gradle:  
Add `maven { url 'https://jitpack.io' }` resposity and `classpath 'com.github.MEiDIK:Cipher.so:dev-SNAPSHOT'` dependency into the buildscript:

```groovy
buildscript {
    repositories {
        google()
        maven { url 'https://jitpack.io' }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.0.1'
        classpath 'com.github.MEiDIK:Cipher.so:dev-SNAPSHOT'
    }
}
```

##### Step 2. in the app module build.gradle:
Add `apply plugin:'cipher.so'` **before**(*VERY IMPORTANT*) `apply plugin: 'com.android.application'`

```groovy
apply plugin: 'cipher.so'
apply plugin: 'com.android.application'
```

That's all, Cipher.so is ready to GO.

#### Configuration

In your app module build.gradle, add the follow-like configs to save key-values.

```groovy
cipher.so {
    keys {
        hello {
            value = 'Hello From Cipher.so😊'
        }
        httpsKey {
            value = 'htkdjfkj@https2017now'
        }
        数据库密码 {
            value = '今天天气不错😂😂'
        }
        ...
    }
}
```

Then Rebuild to generate the Java Interface.

#### 3. Call In Java/Kotlin

```Java
String hello = CipherClient.hello();
String httpsKey = CipherClient.httpsKey();
String dbKey = CipherClient.数据库密码();
```


> Sample: [HelloCipherSo](https://github.com/MEiDIK/HelloCipherSo)




## Contribute?

I am very glad for your contributes. Let's make this job awesome.

Here is the contribute workflow from github: [Contribute Guide](https://github.com/openframeworks/openFrameworks/wiki/Code-Contribution-Workflow#workflow)


## Todos
* Encypte data in .so-lib
* Prevent dynamic attacks
    * ~~Check Signature~~
    * More
* Support different Application varients

## References

* [Add C and C++ Code to Your Project](https://developer.android.com/studio/projects/add-native-code.html)
* [Gradle User Guide](https://docs.gradle.org/4.4/userguide/userguide.html)

## Great Thanks to

* [android-api-SecureKeys](https://github.com/saantiaguilera/android-api-SecureKeys) by [Santi Aguilera](https://github.com/saantiaguilera)
* [gradle-android-ribbonizer-plugin](https://github.com/maskarade/gradle-android-ribbonizer-plugin) by [maskarade](https://github.com/maskarade)

-----

## 关于

### 原理?

在编译期，通过gradle配置将Key-value加密打包进native so库，然后通过自动生成的Java接口可以获取相应的数据。

### 特性

* 通过简单的配置把隐私信息加密进native库
* 没有使用反射

---
## 用法

#### 安装
##### Step 1. 在root project的build.gradle中:
在buildscript中添加仓库`maven { url 'https://jitpack.io' }`，添加依赖`classpath 'com.github.MEiDIK:Cipher.so:dev-SNAPSHOT'`:

```groovy
buildscript {
    repositories {
        google()
        maven { url 'https://jitpack.io' }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.0.1'
        classpath 'com.github.MEiDIK:Cipher.so:dev-SNAPSHOT'
    }
}
```

##### Step 2. 在目标模块的build.gradle中:
在`apply plugin: 'com.android.application'`**前**(**十分重要**)添加`apply plugin:'cipher.so'`

```groovy
apply plugin: 'cipher.so'
apply plugin: 'com.android.application'
```

至此，Cipher.so已经就绪。

#### 配置

在app模块的build.gradle中，通过以下的配置保存key-value值。

```groovy
cipher.so {
    keys {
        hello {
            value = 'Hello From Cipher.so😊'
        }
        httpsKey {
            value = 'htkdjfkj@https2017now'
        }
        数据库密码 {
            value = '今天天气不错😂😂'
        }
        ...
    }
}
```

然后Rebuild一下，自动生产Java的调用接口。

#### 3. 在Java/Kotlin中调用

```Java
String hello = CipherClient.hello();
String httpsKey = CipherClient.httpsKey();
String dbKey = CipherClient.数据库密码();
```


> 例子: [HelloCipherSo](https://github.com/MEiDIK/HelloCipherSo)




## 贡献代码?


十分欢迎你的贡献，让我们一起把这个做得更好。

这是Github的贡献指南: [Contribute Guide](https://github.com/openframeworks/openFrameworks/wiki/Code-Contribution-Workflow#workflow)

## Todos
* 在.so-lib中加密数据
* 防止动态攻击
    * ~~检查应用 签名~~
    * 更多
* 支持Multi Application varients

## 相关资料

* [Add C and C++ Code to Your Project](https://developer.android.com/studio/projects/add-native-code.html)
* [Gradle User Guide](https://docs.gradle.org/4.4/userguide/userguide.html)

## 万分感谢

* [android-api-SecureKeys](https://github.com/saantiaguilera/android-api-SecureKeys) by [Santi Aguilera](https://github.com/saantiaguilera)
* [gradle-android-ribbonizer-plugin](https://github.com/maskarade/gradle-android-ribbonizer-plugin) by [maskarade](https://github.com/maskarade)

-----

## License

    Copyright 2017 认真的帅斌

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
