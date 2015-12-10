---
layout: post
title: android学习记录
date: 2015-12-10T16:40:44.000Z
categories: update
---
<img src="/images/fulls/03.jpg" class="fit image"> 
## 1.client和服务器端交互 ##
![](http://note.youdao.com/share/?id=28272f1e297b0db714e8db8377ea98e8&type=note)

## 2，json的定义和原理 ##
SON 语法是 JavaScript 对象表示语法的子集。
数据在名称/值对中
数据由逗号分隔
花括号保存对象
方括号保存数组

## 3，Gson将json字符串转化为对象 ##
[http://www.2cto.com/kf/201409/339504.html](http://www.2cto.com/kf/201409/339504.html)

## 4，listView必须有Adapter。view重用原理 ##
[http://www.open-open.com/lib/view/open1339485728006.html](http://www.open-open.com/lib/view/open1339485728006.html)
adapter的底端刷新：[http://bbs.9ria.com/thread-237384-1-1.html](http://bbs.9ria.com/thread-237384-1-1.html)

## 5，active生命周期： ##
![](http://note.youdao.com/share/?id=28272f1e297b0db714e8db8377ea98e8&type=note)

## 6,获得  LayoutInflater 实例的三种方式 ##
[http://www.cnblogs.com/devinzhang/archive/2011/12/31/2308812.html](http://www.cnblogs.com/devinzhang/archive/2011/12/31/2308812.html)
** 1. **
`LayoutInflater inflater = getLayoutInflater();  //调用Activity的getLayoutInflater()`
 **2. **
    LayoutInflater localinflater =(LayoutInflater)context.getSystemService (Context.LAYOUT_INFLATER_SERVICE);
** 3.  **
`LayoutInflater inflater = LayoutInflater.from(context);`  
**结论：**
所以这三种方式最终本质是都是调用的Context.getSystemService()。
**注意：**
**·inflate方法与  findViewById 方法不同；**
**·inflater  是用来找 res/layout下的 xml 布局文件，并且实例化；**
**·findViewById()  是找具体 xml 布局文件中的具体 widget 控件**

(如:Button、TextView 等)。
setContentView()一旦调用, layout就会立刻显示UI；而inflate只会把Layout形成一个以view类实现成的对象，有需要时再用setContentView(view)显示出来。

一般在activity中通过setContentView()将界面显示出来，但是如果要在非activity中如何对控件布局进行设置操作，就需LayoutInflater动态加载。

## 7,layout_weight作用 ##
[http://mobile.51cto.com/abased-375428.htm](http://mobile.51cto.com/abased-375428.htm)
[http://www.cnblogs.com/angeldevil/archive/2012/04/08/2437747.html](http://www.cnblogs.com/angeldevil/archive/2012/04/08/2437747.html)

Layout_weight是用LinearLayout的宽度减去子容器的宽度和，再分配    
`int share = (int) (childExtra * delta / weightSum);
int childWidth = child.getMeasuredWidth() + share;`

## 8,选择器四种的使用状态 ##
android:state_focused
android:state_pressed
android:state_selected
android:state_enabled

## 9.广播机制 ##
http://www.cnblogs.com/lwbqqyumidi/p/4168017.html
http://www.cnblogs.com/sunzn/archive/2013/02/13/2910899.html

## 10.viewpager ##
http://blog.csdn.net/wangjinyu501/article/details/8169924/
http://www.open-open.com/lib/view/open1328833592437.html

## 11，TabHost  ##
http://www.open-open.com/lib/view/open1330697955842.html
http://blog.csdn.net/xinem/article/details/7083523
http://www.open-open.com/lib/view/open1379859586226.html
http://www.360doc.com/content/12/0514/19/7857928_211009300.shtml

## 12，给LinearLayout增加事件监听 ##
android:clickable="true" 
http://blog.csdn.net/zanfeng/article/details/41172871

## 13，在OnCreate方法中获取View组件的高度 ##
http://download.csdn.net/detail/bluceshang/5272094
http://ask.csdn.net/questions/11141

## 14,SharedPreferences ##
http://www.jb51.net/article/31911.htm

## 15，动态设置组件高度 ##
    LinearLayout.LayoutParams layoutParams = (LinearLayout.LayoutParams)listView.getLayoutParams();
LinearLayout是其父组件，包裹其的组件
http://blog.csdn.net/penglijiang/article/details/7828036
http://blog.csdn.net/pathuang68/article/details/6647716

## 16，动态更新listView ##
http://dyingbleed.iteye.com/blog/1225284

## 17，ScrollView兼容ListView ##
http://www.apkbus.com/android-11540-1.html    主要是第四种方法
18，pulltorefresh
http://www.tuicool.com/articles/RvQVFbb
19，handler
handler类主要是发送和获取处理消息。handle发送消息给MessageQueen，looper.loop轮询MessageQueen再发送给handle,msg.target.dispatchMessage(msg);
自定义线程使用handle      handleMessage方法是在子线程中进行的

http://www.jb51.net/article/43360.htm
20，Timer
http://blog.csdn.net/ahxu/article/details/249610
http://zengzhaoshuai.iteye.com/blog/1121105
TimeTask本质是启动一个新的线程，由于安卓不允许新线程访问访问Activity里的界面组件，只能发送个消息.
handle.sendEmptyMessage(0x123);
21，判断ScrollView滚到底端或顶端
http://blog.csdn.net/wangbole/article/details/9836771
22，双击退出
http://stackoverflow.com/questions/8430805/android-clicking-twice-the-back-button-to-exit-activity
tabHost中重写dispatchKeyEvent方法，拦截KeyEvent。
23,ViewTreeObserver
http://blog.csdn.net/pathuang68/article/details/6431035
http://www.tuicool.com/articles/fi6BJ3N
24,DisplayMetrics
http://www.eoeandroid.com/thread-246188-1-1.html
25,获取控件的坐标
http://blog.csdn.net/sjf0115/article/details/7306284
26，viewPager适应scrollView
http://www.cnblogs.com/xitang/archive/2013/06/22/3150380.html
if(Math.abs(deltaY) < Math.abs(deltaX)){
    getParent().requestDisallowInterceptTouchEvent(true);
}
27,Android Activity的四种启动模式（回退栈）
http://www.51testing.com/html/34/361634-859805.html
http://blog.csdn.net/tiancizhenai/article/details/7037787
setFlags();http://blog.csdn.net/getchance/article/details/8444589
http://blog.sina.com.cn/s/blog_6dc41baf0101026d.html
28,调用拍照功能
http://hxdawxyhxdawxy.iteye.com/blog/1452747
http://www.cnblogs.com/mengdd/archive/2013/03/31/2991932.html
http://blog.csdn.net/bill_ming/article/details/7730305
29，SQLite
http://www.cnblogs.com/Excellent/archive/2011/11/19/2254888.html
30，AutoCompleteTextView
http://www.cnblogs.com/linjiqin/archive/2011/02/22/1960890.html
http://blog.csdn.net/iamkila/article/details/7230160
31，startactivityforresult()
http://liangoogle.iteye.com/blog/1114642
32,半透明主题
http://blog.csdn.net/ilysony/article/details/6268245
33，ToggleButton
android:button="@drawable/auto_hb_selector"    自定义button样式
setOnCheckedChangeListener 监听变化
34，Service
http://blog.csdn.net/ryantang03/article/details/7770939


35，onNewIntent  单顶模式调用  launchmode="singleTask"
http://blog.csdn.net/java2009cgh/article/details/7000821,

36，Android自定义属性时TypedArray的使用方法
http://www.2cto.com/kf/201302/189492.html
http://blog.csdn.net/richerg85/article/details/11749421

37,自定义View组件
http://www.cnblogs.com/0616--ataozhijia/p/4003380.html

38，页面跳转动画效果
http://www.jb51.net/article/39026.htm

39,android单帧动画Rotate旋转
http://fzlihui.iteye.com/blog/1151630

40，shape的使用
http://www.cnblogs.com/cyanfei/archive/2012/07/27/2612023.html

41，Android里Scroller类的简单用法
http://ipjmc.iteye.com/blog/1615828

42，android Notification 的使用
http://www.cnblogs.com/newcj/archive/2011/03/14/1983782.html

43,Android Studio下jni应用
使用前提：建立同样的包名和类名。
http://blog.csdn.net/sodino/article/details/41946607
http://www.cnblogs.com/flyme/p/4431762.html
http://blog.csdn.net/rznice/article/details/42295215

44，网络工具——Volley（一）
http://blog.csdn.net/airk000/article/details/38983051
http://blog.csdn.net/lmj623565791/article/details/24589837

45,SpannableString与SpannableStringBuilder
http://blog.csdn.net/harvic880925/article/details/38984705

46，测试类

使用断点

47,红点的使用，BadgeView使用介绍
http://blog.csdn.net/a57565587/article/details/11097679

48，属性动画
http://blog.csdn.net/guolin_blog/article/details/43536355
http://blog.csdn.net/lmj623565791/article/details/38067475

49,Android RecyclerView 使用完全解析 体验艺术般的控件
http://blog.csdn.net/lmj623565791/article/details/45059587

50.Android图像处理之Bitmap类
http://blog.csdn.net/thl789/article/details/6762030
设定背景的可以用在主题中设置，减少重复渲染
<style  
        name="Theme.Default.NoActionBar"  
        parent="@android:style/Theme.Holo.Light.NoActionBar" >  
        <item name="android:windowBackground">@drawable/login</item>  
    </style> 

51,自定义控件其实很简单1/3
http://blog.csdn.net/aigestudio/article/details/41799811

