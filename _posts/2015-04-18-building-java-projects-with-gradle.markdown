---
layout: post
title:  "สร้างโปรเจ็ค Java ด้วย Gradle"
date:   2015-04-18 14:22:22
categories: java project gradle
---

## ติดตั้ง Gradle

1. เข้าไปโหลดที่ [Gradle](http://gradle.org/downloads) จะได้ไฟล์ `gradle-version-bin.zip`
2. แตก zip
3. set path ไปที่แตก zip

ทดสอบการติดตั้ง Gradle โดยเปิด command-line แล้วรัน

~~~
gradle
~~~

จะมี message ต้อนรับขึ้นมา `Welcome to Gradle 2.3. ... BUILD SUCCESSFUL`

## สร้าง directory ของโปรเจ็ค

~~~
<your directory>
└─ src
   └─ main
      └─ java
         └─ hello
            └─ HelloWorld.java
~~~

ไฟล์ `HelloWorld.java`

{% highlight java %}
package hello;

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello world!!");
    }
}
{% endhighlight %}

## Build it!!!

สร้างไฟล์ `build.gradle` แล้วเพิ่มปลั๊กอิน java เข้าไป

~~~
apply plugin: 'java'
~~~

เสร็จแล้วรัน

~~~
gradle build
~~~

จะได้ `HelloWorld.class`

~~~
<your directory>
└─ src
   └─ main
      └─ java
         └─ hello
            └─ HelloWorld.java
└─ build
   └─ classes
      └─ main
         └─ hello
            └─ HelloWorld.class
build.gradle
~~~

เพิ่มปลั๊กอิน application ใน `build.gradle` *เพื่อให้เวลารันแอพแล้วมันจะวิ่งเข้า* `main method`

~~~
apply plugin: 'application'
mainClassName = 'hello.HelloWorld'
~~~

เสร็จแล้วรัน build (อีกรอบ)

~~~
gradle build
~~~

ข้อความ `... BUILD SUCCESSFUL` จะขึ้นมา

เสร็จแล้วรันแอพ

~~~
gradle run
~~~

~~~
:compileJava UP-TO-DATE
:processResources UP-TO-DATE
:classes UP-TO-DATE
:run
Hello world!!

BUILD SUCCESSFUL
~~~
