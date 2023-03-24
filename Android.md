Target: Android

# 1、C# 调用 Java

Java端的实现：

可用一个Java类，比如单例（有getInstance()方法），在里面实现对应供C#使用的方法。这样C#端就只要这样：

AndroidJavaClass jc = new AndroidJavaClass("com.company.package.class"); // java.lang.class
AndroidJavaObject jo = jc.GetStatic<AndroidJavaObject>("getInstance");   // java.lang.object

//上面这里是利用java的反射，得到某个类的实例

jo.Call("method1"); //method1是上面单例的无参数方法


# 2、Java 调用 C#

只有一条路径，unity实现了java的类

com.unity3d.player 包中，有

UnityPlayerActivity.java 类，

其中有UnityPlayer成员，该成员有SendMessage()方法与C#沟通

所以，整体是

com.unity3d.player.UnityPlayer.UnitySendMessage(gameobject, methodname, parameter)

能调用到场景中的GameObject上的方法，并能带一个字符串参数