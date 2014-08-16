HeaderGridView
==============

A GridView with header / footer support.

```java
gridView.addHeaderView(view)
```

Why?
---

Standard GridView does not support HeaderView. Once we want to add a header to GridView, we have to do some hack.

```java
@Override
public View getView(int position, View convertView, ViewGroup parent) {
    // deal with convertView
    
    if (position < mNumberOfColumns) {
      // return Header Views  
    } else {
      // return a view of position: (position - mNumberOfColumns)
    }
}

@Override
public Object getItem(int position) {
    return (position < mNumberOfColumns) ? null : items.get(position - mNumberOfColumns);
}
```

This hack is so dirty. Every `position` you have to write `position - mNumberOfColumns`. If you forget it, it will occur something unexpected!

And `getItem(position)` sometime returns `null`. Really dangerous.

However, the library aims to solve this headache.

With HeaderGridView
---

```java
@Override
public View getView(int position, View convertView, ViewGroup parent) {
    // just deal with convertView and return a View
}

@Override
public Object getItem(int position) {
    return items.get(position);
}
```

The code looks like ordinary `GridView`. Yes.

You have to do just `gridView.addHeaderView(view)` to add a header view!

Status
---

Currently WIP! :laughing:
