# 1、多任务和进程、多线程的关系

1. 多任务

   多任务指的是：多个事情都在做，但实际上是逐一处理，可能只是切换的速度很快

2. 进程和多线程

   一个进程中可以包含多个线程：进程就像是线缆壳，而真正执行的是线程，多个线程之间是同时运行的

   > 另外名词区分：
   >
   > 程序和进程，程序指数据和指令的集合，是一个整体上的概念，进程指的是一次程序运行的过程，一个正在运行的程序的意思

   java程序在运行时，即使没有自己创建线程，后台也会有多个线程，入主线程和gc线程（垃圾回收线程）

   如果开辟了多个线程，线程的运行最终由调度器安排调度，调度器是与操作系统紧密相关的，先后顺序无法人为干预
   
   对同一份资源进行操作时，会存在资源抢夺的问题，需要加入并发控制
   
   线程会带来额外的开销，比如cpu调度时间，并发控制开销
   
   每个线程在自己的工作内存交互，内存控制不当可能会造成数据不一致





# 2、实现多线程



## 2.1、继承Thread类

继承Thread类之后重写run方法作为方法体，run方法为运行，start为启动线程

```java
public void TestThread extends Thread{
    @Override
    public void run(){
        //方法体
    }
}
public static void main(String[] args){
    TestThread testThread = new TestThread();
    testThread.start();
}
```



## 2.1.1、多线程下载器

> 工具类 commons io

```java
import org.apache.commons.io.FileUtils;

import java.io.File;
import java.io.IOException;
import java.net.URL;

class WebDownloader{
    public void download(String url,String name){
        try{

            FileUtils.copyURLToFile(new URL(url),new File(name));

        }catch(IOException e){
            e.printStackTrace();
        }
    }
}

class ThreadDownloadTest extends Thread{
    private String url;
    private String name;

    public ThreadDownloadTest(String url,String name){
        this.url=url;
        this.name=name;
    }

    @Override
    public void run(){
        WebDownloader webDownloader = new WebDownloader();
        webDownloader.download(url,name);
        System.out.println("download complete:"+name);
    }

    public static void main(String[] args){
        ThreadDownloadTest t1 = new ThreadDownloadTest("https://pixivic.com/?VNK=a342deb4//img//icon.9a42bbfa.svg","1.svg");
        ThreadDownloadTest t2 = new ThreadDownloadTest("https://pixivic.com/?VNK=a342deb4//img//icon.9a42bbfa.svg","2.svg");

        t1.start();
        t2.start();
    }
}
```





## 2.2、实现Runnable接口

开启线程的另一种方法是实现Runnable接口

不过在调用start的时候方法不太一样，需要传实现接口类再调start方法

```java
TestThread testThread = new TestThread();
new Thread(testThread).start();
```

