![BetterPickers Feature Graphic][5]

DialogFragments modeled after the 4.2 Alarm Clock TimePicker to improve UX for picking time, date, and numbers.

Try out the sample application on [Google Play][6].

<a href="https://play.google.com/store/apps/details?id=com.doomonafireball.betterpickers.sample">
  <img alt="BetterPickers Samples on Google Play"
         src="http://developer.android.com/images/brand/en_app_rgb_wo_45.png" />
</a>

Changelog
=========

**1.3.1**
* Improve UX for min/max for NumberPicker
* Added ListView demos to the sample app

**1.3.0**

* Add Catalan, Spanish
* Enable min/max for NumberPicker
* Added Javadoc comments
* Added universal handlers
* Added picker references
* UX tweak for DatePicker indicator

**1.2.0**

* Removed some unused fonts from sample/ project
* Refactor to Builder pattern
* Fix for Gingerbread font in DatePicker
* Added optional label text to NumberPicker
* DatePicker reorders text and keyboards based on locale
* NumberPicker scrolls horizontally to allow for more numbers

**1.1.0**

* Added HMS (hours:minutes:seconds) PickerFragment
* Allow for PickerFragments within target fragments
* Allow for February 29th input

Including in Your Project
=========================

Android-BetterPickers is presented as an [Android library project][7]. A
standalone JAR is not possible due to the theming capabilities offered by the DialogFragments.

You can include this project by [referencing it as a library project][8] in
Eclipse or ant.  Note that to use this library, both it and your project must be compiled with Android 4.0 (API level 14) or newer, similar to ActionBarSherlock.

If you are a Maven user you can easily include the library by specifying it as
a dependency:

    <dependency>
      <groupId>com.doomonafireball.betterpickers</groupId>
      <artifactId>library</artifactId>
      <version>1.3.1</version>
      <type>apklib</type>
    </dependency>

This project depends on Jake Wharton's `ViewPagerIndicator` library. Details for
including this library are available [here][9].

Usage
=====

*For a working implementation of this project see the `sample/` folder.*

  0. Include the Android clock fonts in your `assets/fonts/` folder (create the folder if it doesn't already exist.  You can find these fonts in the `sample/assets/fonts/` folder.

        Roboto-Bold.ttf
        AndroidClockMono-Thin.ttf

  1. Implement the appropriate Handler callbacks:

        public class MyActivity extends Activity implements DatePickerDialogFragment.DatePickerDialogHandler {
        
          @Override
          public void onCreate(Bundle savedInstanceState) {
            // ...
          }
          
          @Override
          public void onDialogDateSet(int year, int monthOfYear, int dayOfMonth) {
            // Do something with your date!
          }
        }  

  2. Use one of the Builder classes to create a PickerDialog with a theme:

        DatePickerBuilder dpb = new DatePickerBuilder()
            .setFragmentManager(getSupportFragmentManager())
            .setStyleResId(R.style.BetterPickersDialogFragment);
        dpb.show();

Theming
=======

*For a demonstration of theming, see the `sample/` folder.*

You can use your own themes if you'd like to change certain attributes.  BetterPickers currently allows for customization of the following attributes:

        bpDialogBackground       :: the drawable (preferably a 9-patch) used as a window background for the DialogFragment
        bpTextColor              :: the color (optionally state list) for all text in the DialogFragment
        bpDeleteIcon             :: the drawable (optionally state list) for the delete button
        bpCheckIcon              :: the drawable (optionally state list) for the check button in the DateDialogPicker
        bpKeyBackground          :: the drawable (optionally state list) for the keyboard buttons
        bpButtonBackground       :: the drawable (optionally state list) for the Set, Cancel, and Delete buttons
        bpDividerColor           :: the color used for the DialogFragment dividers
        bpKeyboardIndicatorColor :: the color used for the ViewPagerIndicator on the DateDialogPicker

  1. Create your own custom theme in `styles.xml`:

        <style name="MyCustomBetterPickerTheme">
            <item name="bpDialogBackground">@drawable/custom_dialog_background</item>
            <item name="bpTextColor">@color/custom_text_color</item>
            <item name="bpDeleteIcon">@drawable/ic_backspace_custom</item>
            <item name="bpCheckIcon">@drawable/ic_check_custom</item>
            <item name="bpKeyBackground">@drawable/key_background_custom</item>
            <item name="bpButtonBackground">@drawable/button_background_custom</item>
            <item name="bpDividerColor">@color/custom_divider_color</item>
            <item name="bpKeyboardIndicatorColor">@color/custom_keyboard_indicator_color</item>
        </style>
        
  2. Instantiate your `DialogFragment` using your custom theme:

        DatePickerBuilder dpb = new DatePickerBuilder()
            .setFragmentManager(getSupportFragmentManager())
            .setStyleResId(R.style.MyCustomBetterPickerTheme);
        dpb.show();

Contribution
============

### Pull requests are welcome!

Feel free to contribute to BetterPickers.

If you've fixed a bug or have a feature you've added, just create a pull request.

If you've found a bug, want a new feature, or have other questions, [file an issue][10]. I'll try to answer as soon as I find the time.

Credits
=======

Thanks to [JakeWharton][11] for his work on [ViewPagerIndicator][9].

Thanks to [OAK][12] and [WillowTree Apps][13] for Maven assistance and possible future improvements.

License
=======

    Copyright 2013 Derek Brameyer

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

 [5]: https://raw.github.com/derekbrameyer/android-betterpickers/master/sample/imagery/web_feature_graphic.png
 [6]: https://play.google.com/store/apps/details?id=com.doomonafireball.betterpickers.sample
 [7]: http://developer.android.com/guide/developing/projects/projects-eclipse.html
 [8]: http://developer.android.com/guide/developing/projects/projects-eclipse.html#ReferencingLibraryProject
 [9]: http://viewpagerindicator.com/
 [10]: https://github.com/derekbrameyer/android-betterpickers/issues/new
 [11]: https://plus.google.com/108284392618554783657/posts
 [12]: http://willowtreeapps.github.io/OAK/
 [13]: http://www.willowtreeapps.com/
