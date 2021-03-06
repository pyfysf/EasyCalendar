# EasyCalendar

Quickly customize the calendar UI. You can use `EasyCalendar` to quickly get the calendar style UI.

# Feature

* Custom layout for title.
* Custom layout for date.
* Show or hide divider for date.
* Show or hide overflow date.
* Listen to date's view be clicked.

# Screenshot

<img src="https://github.com/shichaohui/EasyCalendar/blob/master/screeshot/screenshot_main_gif.gif" width = "270" alt="默认样式" />  <img src="https://github.com/shichaohui/EasyCalendar/blob/master/screeshot/screenshot_action.jpg" width = "270" alt="自定义样式" />

<img src="https://github.com/shichaohui/EasyCalendar/blob/master/screeshot/screenshot_checkin_gif.gif" width = "270" alt="自定义样式" /> <img src="https://github.com/shichaohui/EasyCalendar/blob/master/screeshot/screenshot_checkin.jpg" width = "270" alt="自定义样式" />

# Gradle

```
compile 'com.sch.calendar:easy-calendar:1.0.1'
```

# Attributes
| name | format | description |
|:----|:----|:----|
| titleColor | color | set color for title |
| titleLayout | reference | custom layout for title |
| weekColor | color | set color for week |
| weekBackground | color\|reference | set background for week bar |
| monthBackground | color\|reference | set backgroung for month layout |
| dateDividerColor | color | set color for divider of date |
| dateDividerSize | dimension | set size for divider of date |
| imgLastMonth | reference | set image for button of last month |
| imgNextMonth | reference | set image for button of next month |
| language | enum | china: 中文, english: English |

# API

1. Show or hide overflow date.
```java
/**
 * If true, show whole calendar.
 * e.g. showing date is April, if show whole calendar, 03/30 and 05/01 will show.
 */
public void setShowOverflowDate(boolean showOverflowDate);

public boolean isShowOverflowDate();
```

2. Set format for title.
```java
/**
 * Constructs a <code>SimpleDateFormat</code> using the given pattern and
 * the default date format symbols for the given locale.
 * <b>Note:</b> This constructor may not support all locales.
 * For full coverage, use the factory methods in the {@link DateFormat}
 * class.
 *
 * @param pattern the pattern describing the date and time format
 * @param locale  the locale whose date format symbols should be used
 */
public void setTitleFormat(String pattern, Locale locale);
```

3. Set a listener for callback when date was clicked.
```java
/**
 * Set listener for date be clicked.
 *
 * @param onDateClickedListener listener
 */
public void setOnDateClickedListener(OnDateClickedListener onDateClickedListener);
```

4. Set a listener for callback when showing month changed.
```java
/**
 * Set listener for current showing month changed.
 *
 * @param onMonthChangedListener listener
 */
public void setOnMonthChangedListener(final OnMonthChangedListener onMonthChangedListener);
```

5. Set can or can't change month by drag.
```java
/**
 * Set drag enable for page.
 */
public void setCanDrag(boolean canDrag);

/**
 * Return drag enable of page.
 */
public boolean canDrag();
```

6. Set can or can't fling when finger off screen.
```java
/**
 * Set fling enable for page.
 */
public void setCanFling(boolean canFling);

/**
 * Return fling enable of page.
 */
public boolean canFling();
```

7. Set the visibility of the button for the month of switch.
```java
/**
 * Set button visible for last month.
 *
 * @param visibility {@link Visibility}
 */
public void setLastMonthButtonVisibility(@Visibility int visibility);

/**
 * Set button visible for next month.
 *
 * @param visibility {@link Visibility}
 */
public void setNextMonthButtonVisibility(@Visibility int visibility);
```

8. Get view of today.
```java
/**
 * Return item view of today. If today not showing, return null。
 */
public View getTodayItemView();
```

9. Set the calendar size will wrap content or not.
Use this api you can set the calendar size will wrap content or not. if true, the layout's height will auto change with animation when month changed.
```java
/**
 * Set the layout will wrap content or not.
 *
 * @param scaleEnable if true, the layout will wrap content.
 */
public void setScaleEnable(boolean scaleEnable);
```

# Custom UI for date

You can use default UI for date by [SampleVagueAdapter](https://github.com/shichaohui/EasyCalendar/blob/master/library/src/main/java/com/sch/calendar/adapter/SampleVagueAdapter.java). Default UI only show date.
```java
calendarView.setVagueAdapter(new SampleVagueAdapter());
```

You can custom UI for date by extend [VagueAdapter](https://github.com/shichaohui/EasyCalendar/blob/master/library/src/main/java/com/sch/calendar/adapter/VagueAdapter.java) , e.g. custom UI for checkin.
```java

// layout_checkin_calendar_item must hava a TextView that's id is tv_day_of_month
calendarView.setVagueAdapter(new MyVagueAdapter(R.layout.layout_checkin_calendar_item));

private class MyVagueAdapter extends VagueAdapter<Map<String, Map<String, Checkin>>> {

    /**
     * @params dateLayout layout resource id for date, must hava a TextView that's id is tv_day_of_month
     */
    MyVagueAdapter(@LayoutRes int dateLayout) {
        super(dateLayout);
    }

    @Override
    public void onBindVague(View itemView, int year, @Month int month, @DayOfMonth int dayOfMonth) {
        // do something, show custom data  
    }

    @Override
    public void flagToday(View todayView) {            
        // do something, set a flag for today's view
    }

    @Override
    public void flagNotToday(View dayView, Date date) {
       // do something, set a flag for not today's view
    }
}
```

# License

```
 Copyright 2017 StoneHui
 
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 
      http://www.apache.org/licenses/LICENSE-2.0
 
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and limitations under the License.
 ```
