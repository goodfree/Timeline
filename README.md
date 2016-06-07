# Timeline-View 

Android Timeline View Library (Using RecyclerView) is simple implementation used to display view like Tracking of shipment/order, steppers etc.

[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-Timeline--View-brightgreen.svg?style=flat)](http://android-arsenal.com/details/1/2923)

[![Android Gems](http://www.android-gems.com/badge/vipulasri/Timeline-View.svg)](http://www.android-gems.com/lib/vipulasri/Timeline-View?lib_id=773)

### Screenshot of Sample Application

[Sample Application Apk](https://github.com/vipulasri/Timeline-View/tree/master/apk)

![Screenshot](https://github.com/vipulasri/Timeline-View/blob/master/Screenshot1.png)

![Screenshot](https://github.com/vipulasri/Timeline-View/blob/master/Screenshot2.png)

## Quick Setup

### 1. Include library

**Using Gradle**

``` gradle
dependencies {
    compile 'com.github.vipulasri:timelineview:1.0.3'
}
```

**Using Maven**

``` maven
<dependency> 
    <groupId>com.github.vipulasri</groupId> 
    <artifactId>timelineview</artifactId> 
    <version>1.0.3</version> 
    <type>pom</type> 
</dependency>
```


#### Manual:
**Manual - Using [Android Studio](https://developer.android.com/sdk/installing/studio.html):**
 * Download the library folder and import to your root application folder. 
You can manually achieve this step with 3 steps: 
    1. Paste the folder library into your application at the same level of your app, build and gradle folder
    2. Add to your settings.gradle file the following code line:
    "include ':app', ':timelineview'"
    3. Rebuild the project
 * File → Project Structure → in Modules section click on "app" → Click on tab "Dependecies" → Click on the green plus → Module Dependecy → Select ":library"
 * Done 
 
### What's New

See the project's Releases page for a list of versions with their changelogs.

### [View Releases](https://github.com/vipulasri/Timeline-View)

If you Watch this repository, GitHub will send you an email every time I publish an update.
 
### 2. Usage
 
 * In XML Layout : 
 
 ``` java
<com.vipul.hp_hp.timelineview.TimelineView
    android:id="@+id/time_marker"
    android:layout_width="wrap_content"
    android:layout_height="match_parent"
    app:marker_size="25dp"
    app:line_size="2dp"
    app:line="@color/colorPrimary"/>
```

* Configure using xml attributes or setters in code:

    <table>
    <th>Attribute Name</th>
    <th>Default Value</th>
    <th>Description</th>
    <tr>
        <td>app:marker="@drawable/marker"</td>
        <td>Green Colored Oval Drawable</td>
        <td>sets marker drawable</td>
    </tr>
    <tr>
        <td>app:marker_size="25dp"</td>
        <td>25px</td>
        <td>sets marker size</td>
    </tr>
    <tr>
        <td>app:markerInCenter="false"</td>
        <td>true</td>
        <td>sets the marker in center of line if `true`</td>
    </tr>
    <tr>
        <td>app:line="@color/primarColor"</td>
        <td>N/A</td>
        <td>Compulsory Field - set line color</td>
    </tr>
     <tr>
        <td>app:line_size="2dp"</td>
        <td>2px</td>
        <td>sets line width</td>
    </tr>
    <tr>
        <td>app:line_orientation="horizontal"</td>
        <td>vertical</td>
        <td>sets orientation of line ie `horizontal` or `vertical`</td>
    </tr>
    </table>
 
 
 * RecyclerView Holder : 
   Your `RecyclerViewHolder` should have an extra paramenter in constructor i.e viewType from `onCreateViewHolder`. You would also have to call the method `initLine(viewType)` in constructor definition.
 
``` java

    public class TimeLineViewHolder extends RecyclerView.ViewHolder {
        public  TimelineView mTimelineView;

        public TimeLineViewHolder(View itemView, int viewType) {
            super(itemView);
            mTimelineView = (TimelineView) itemView.findViewById(R.id.time_marker);
            mTimelineView.initLine(viewType);
        }
    }

```

* RecyclerView Adapter : 
   override `getItemViewType` method in Adapter
 
``` java

    @Override
    public int getItemViewType(int position) {
        return TimelineView.getTimeLineViewType(position,getItemCount());
    }

```
   And pass the `viewType` from `onCreateViewHolder` to its Holder.
   
``` java

    @Override
    public TimeLineViewHolder onCreateViewHolder(ViewGroup parent, int viewType) {
        View view = View.inflate(parent.getContext(), R.layout.item_timeline, null);
        return new TimeLineViewHolder(view, viewType);
    }

```


For information : checkout [sample app](https://github.com/vipulasri/Timeline-View/tree/master/app) in repository.


## License


    The MIT License (MIT)

    Copyright (c) 2015 Vipul Asri

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in
    all copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
    THE SOFTWARE.
