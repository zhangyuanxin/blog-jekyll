---
layout: post
title: Android ListView
comments: true
author:  张远馨
categories: 
  - code
tags:
  - android
image: https://unsplash.it/2000/1200?image=163
image-sm: https://unsplash.it/500/300?image=163

---

**Android ListView 无数据视图**


ListView继承了AdapterView公共方法`setEmptyView`：


```java
// Sets the view to show if the adapter is empty
public void setEmptyView (View emptyView)

```

这是ListView无数据时显示的视图，当Adapter为空或者无数据的时候显示，可是直接这样做并没有什么效果。

做法一：


无数据的布局文件代码：

```xml
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
            android:src="@drawable/no_data" />
        <TextView 
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textColor="#ffafafaf"
            android:textSize="18sp"
            android:layout_marginTop="8dp"
            android:text="什么都没有哦~" />
    </LinearLayout>
</RelativeLayout>
```

布局文件代码：
```xml
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
```

Activity代码：

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_listview);

    ListView listView = (ListView) findViewById(R.id.list);
    listView.setEmptyView(findViewById(R.id.layout_empty));
}
```

做法二：

布局文件代码：

```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >
    <ListView 
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:id="@+id/list" />
</RelativeLayout>
```

Activity代码：

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_listview);
    ListView listView = ((ListView) findViewById(R.id.list));
    View listEmptyView = View.inflate(this, R.layout.layout_empty, (ViewGroup) listView.getParent());
    listView.setEmptyView(listEmptyView);
}
```

有数据时相当于如下操作：
```java
listView.setVisibility(View.VISIBLE);
listEmptyView.setVisibility(View.GONE);
```
无数据时如下操作：
```java
listView.setVisibility(View.GONE);
listEmptyView.setVisibility(View.VISIBLE);
```
这样也就能够解释为什么要将listEmptyView添加到listView的同一视图层级上。

它们是两者只显示其一的关系，因此当设置的空数据布局后，listView的header和footer在无数据时候也是不显示的。
