---
layout: post
title: Android Empty ListView
comments: true
author:  张远馨
categories: [Android, ListView]
image: https://unsplash.it/2000/1200?image=163
image-sm: https://unsplash.it/500/300?image=163

---

**Android ListView 无数据视图**

setEmptyView方法无效？

在Android API中可以查到ListView的继承了AdapterView的一个公共的方法

```java

public void setEmptyView (View emptyView)

```

说道： 
> Sets the view to show if the adapter is empty

根据函数名称就很容易判断这是为ListView添加一个无数据时候的视图，当Adapter为空或者无数据的时候显示，可是直接这样做并没有什么效果。

通常做法1

使用到的图片资源ic_none_notice

这里写图片描述

空数据时候的布局文件layout_empty.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <LinearLayout 
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_centerVertical="true"
        android:gravity="center_horizontal"
        android:orientation="vertical" >

        <ImageView 
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_none_notice" />

        <TextView 
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textColor="#ffafafaf"
            android:textSize="18sp"
            android:layout_marginTop="8dp"
            android:text="什么都没有哦~" />

    </LinearLayout>
</RelativeLayout>

主程序视图的布局文件activity_main.xml

<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <ListView 
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/list" />

    <include 
        layout="@layout/layout_empty"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:visibility="gone"
        android:id="@+id/layout_empty" />
</RelativeLayout>

主程序MainActivity.Java的onCreate函数

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    ListView listView = (ListView) findViewById(R.id.list);
    listView.setEmptyView(findViewById(R.id.layout_empty));
}

通常做法2

修改上述的activity_main.xml代码为

<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <ListView 
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/list" />

</RelativeLayout>

修改主程序MainActivity.java的onCreate函数为：

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    ListView listView = ((ListView) findViewById(R.id.list));
    /**
     * 下面的一行代码与可如下两行等价
     * View listEmptyView = View.inflate(this, R.layout.layout_empty, null);
     * ((ViewGroup) listView.getParent()).addView(listEmptyView, -1, -1);
     */
    View listEmptyView = View.inflate(this, R.layout.layout_empty, (ViewGroup) listView.getParent());
    listView.setEmptyView(listEmptyView);
}

运行结果

有数据： 
这里写图片描述

无数据： 
这里写图片描述

原因猜测

实际上在对listView设置了listEmptyView之后，整个界面就变成了

当有数据的时候相当于进行了如下操作：

listView.setVisibility(View.VISIBLE);
listEmptyView.setVisibility(View.GONE);

当无数据或者Adapter为空的时候进行了如下操作：

listView.setVisibility(View.GONE);
listEmptyView.setVisibility(View.VISIBLE);

这样也就能够解释为什么要将listEmptyView添加到listView的同一视图层级上

他们是每次只显示其一的关系，因此当设置的空数据布局之后，listView的header和footer在无数据时候也是不显示的
