# widget


#Create Layout(wetdget_layout.xml)
```bash

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    android:background="@drawable/card1"
    android:layout_margin="@dimen/_5sdp"
    >


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_margin="@dimen/_3sdp"

        >

        <TextView
            android:id="@+id/widget_bangladate"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:fontFamily="@font/kalpurush"
            android:text="১৯ ফাল্গুন"
            android:layout_gravity="center"
            android:textColor="@color/white"
            android:textSize="@dimen/_10ssp" />

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:layout_marginStart="@dimen/_5sdp"
            android:fontFamily="@font/kalpurush"
            android:text="১৪৩২"
            android:textColor="@color/white"
            android:textSize="@dimen/_7sdp" />

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"


            >


            <ImageView
                android:layout_width="@dimen/_15sdp"
                android:layout_height="@dimen/_15sdp"
                android:layout_gravity="end"
                android:layout_marginRight="@dimen/_10sdp"
                android:src="@drawable/bangladesh" />

            <TextView
                android:id="@+id/bangladeshTv"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_gravity="end|center_horizontal"
                android:layout_marginRight="@dimen/_8sdp"
                android:fontFamily="@font/solaimanlipi"
                android:text="বাংলাদেশ"
                android:textSize="@dimen/_5sdp"
                android:textColor="@color/blue" />

        </LinearLayout>

    </LinearLayout>


    <TextView
        android:id="@+id/widget_engdate"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="সোমবার, ২০ ফাল্গুন ১৪৩১"
        android:textColor="@color/white"
        android:fontFamily="@font/kalpurush"
        android:textSize="@dimen/_11sdp"
        android:layout_marginStart="@dimen/_5sdp"
        android:layout_marginBottom="@dimen/_5sdp"
        />


    <TextView
        android:id="@+id/widget_sunrise"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@drawable/sunrise"

        android:drawablePadding="@dimen/_10sdp"
        android:elevation="@dimen/_15sdp"
        android:fontFamily="@font/solaimanlipi"
        android:gravity="center_vertical"
        android:padding="@dimen/_1sdp"
        android:text="সূর্য উদয়- ৯টা১৩মি২৬সে"
        android:textColor="@color/white"
        android:textSize="@dimen/_8sdp"
        android:drawableLeft="@drawable/sun"
        />

    <TextView
        android:id="@+id/widget_sunset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@drawable/sunset"
        android:elevation="@dimen/_15sdp"
        android:fontFamily="@font/solaimanlipi"
        android:text="সূর্যস্তো- ৯টা১৩মি২৬সে"
        android:drawableLeft="@drawable/sun_set"
        android:padding="@dimen/_1sdp"
        android:drawablePadding="@dimen/_10sdp"
        android:gravity="center_vertical"
        android:textColor="@color/white"
        android:textSize="@dimen/_8sdp"
        android:layout_marginTop="@dimen/_5sdp"
        android:layout_marginBottom="@dimen/_5sdp"

        />

    <TextView
        android:id="@+id/widget_detail"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="@font/kalpurush"
        android:text="বিশ্ব হরিনাম দিবস,শ্রীশ্রীমাতা নন্দরাণীর তিরোধাম দিবস"
       android:layout_margin="@dimen/_5sdp"
        android:textColor="@color/white"
        android:textSize="@dimen/_8ssp" />

</LinearLayout>


```

#Make Class(MyWidgetProvider)
``bash

package com.example.calander;

import android.annotation.SuppressLint;
import android.appwidget.AppWidgetManager;
import android.appwidget.AppWidgetProvider;
import android.content.ComponentName;
import android.content.Context;
import android.content.Intent;
import android.widget.RemoteViews;

public class MyWidgetProvider extends AppWidgetProvider {

    public static void updateWidgetText(Context context, String newText,String engDate) {
        AppWidgetManager appWidgetManager = AppWidgetManager.getInstance(context);
        ComponentName widgetComponent = new ComponentName(context, MyWidgetProvider.class);
        int[] widgetIds = appWidgetManager.getAppWidgetIds(widgetComponent);

        @SuppressLint("RemoteViewLayout") RemoteViews views = new RemoteViews(context.getPackageName(), R.layout.widget_layout);
        views.setTextViewText(R.id.widget_bangladate, newText);
        views.setTextViewText(R.id.widget_engdate, engDate);

        appWidgetManager.updateAppWidget(widgetIds, views);
    }

    @Override
    public void onUpdate(Context context, AppWidgetManager appWidgetManager, int[] appWidgetIds) {
        // Default static update if needed
        for (int id : appWidgetIds) {
            @SuppressLint("RemoteViewLayout") RemoteViews views = new RemoteViews(context.getPackageName(), R.layout.widget_layout);
            views.setTextViewText(R.id.widget_bangladate, "আজকের তারিখ");
            appWidgetManager.updateAppWidget(id, views);
        }
    }
}

```

#create class2()
```bash

```

