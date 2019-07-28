WM Sweet Alert Dialog
===================
WMSweetAlert for Android, a beautiful and clever alert dialog

#### This is the most advanced and contemporary fork of the apparently dead project 
**Added:**
- Ability to set custom view
- More convenient interface to bind listeners (like in AlertDialog)
- Third neutral button with own listener, colors, methods and etc.
- Ability to disable buttons
- Ability to set buttons stroke
- Dark style of dialogs
- Ability to make dialogs without buttons
- Support of HTML tags
- Ability to set text size

Some screenshots of the new features:

<img src="https://cloud.githubusercontent.com/assets/10178982/24260517/c6f72da6-0ffc-11e7-9a16-67fea4010a34.jpg" width="30%"/>

<img src="https://user-images.githubusercontent.com/10178982/39063916-3a3db5ce-44d5-11e8-97bc-adb390c2f78a.jpg" width="30%"/>


Inspired by JavaScript [SweetAlert](http://tristanedwards.me/sweetalert)

## Setup
The simplest way to use WMSweetAlertDialog is to add the library as aar dependency to your build.

**Maven**

    <dependency>
      <groupId>org.wmtechnology.wmsweetalert</groupId>
      <artifactId>library</artifactId>
      <version>1.1.3</version>
      <type>aar</type>
    </dependency>

**Gradle**

    repositories {
        mavenCentral()
    }

    dependencies {
        compile 'org.wmtechnology.wmsweetalert:library:1.1.3'
    }

## Usage

show material progress

    WMSweetAlertDialog pDialog = new WMSweetAlertDialog(this, SweetAlertDialog.PROGRESS_TYPE);
    pDialog.getProgressHelper().setBarColor(Color.parseColor("#A5DC86"));
    pDialog.setTitleText("Loading");
    pDialog.setCancelable(false);
    pDialog.show();


You can customize progress bar dynamically with materialish-progress methods via **WMSweetAlertDialog.getProgressHelper()**:
- resetCount()
- isSpinning()
- spin()
- stopSpinning()
- getProgress()
- setProgress(float progress)
- setInstantProgress(float progress)
- getCircleRadius()
- setCircleRadius(int circleRadius)
- getBarWidth()
- setBarWidth(int barWidth)
- getBarColor()
- setBarColor(int barColor)
- getRimWidth()
- setRimWidth(int rimWidth)
- getRimColor()
- setRimColor(int rimColor)
- getSpinSpeed()
- setSpinSpeed(float spinSpeed)


more usages about progress, please see the sample.

A basic message：

    new WMSweetAlertDialog(this)
        .setTitleText("Here's a message!")
        .show();

A title with a text under：

    new WMSweetAlertDialog(this)
        .setTitleText("Here's a message!")
        .setContentText("It's pretty, isn't it?")
        .show();

A error message：

    new WMSweetAlertDialog(this, WMSweetAlertDialog.ERROR_TYPE)
        .setTitleText("Oops...")
        .setContentText("Something went wrong!")
        .show();

A warning message：

    new WMSweetAlertDialog(this, WMSweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setConfirmText("Yes,delete it!")
        .show();

A success message：

    new WMSweetAlertDialog(this, WMSweetAlertDialog.SUCCESS_TYPE)
        .setTitleText("Good job!")
        .setContentText("You clicked the button!")
        .show();

A message with a custom icon：

    new WMSweetAlertDialog(this, WMSweetAlertDialog.CUSTOM_IMAGE_TYPE)
        .setTitleText("Sweet!")
        .setContentText("Here's a custom image.")
        .setCustomImage(R.drawable.custom_img)
        .show();

A message with a custom view：

    final EditText editText = new EditText(this);
    new WMSweetAlertDialog(this, WMSweetAlertDialog.NORMAL_TYPE)
            .setTitleText("Custom view")
            .setConfirmText("Ok")
            .setCustomView(editText)
            .show();


Different ways to bind the listener to button：

    new WMSweetAlertDialog(this, WMSweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setConfirmText("Yes,delete it!")
        .setConfirmClickListener(new WMSweetAlertDialog.OnSweetClickListener() {
            @Override
            public void onClick(WMSweetAlertDialog sDialog) {
                sDialog.dismissWithAnimation();
            }
        })
        .setCancelButton("Cancel", new WMSweetAlertDialog.OnSweetClickListener() {
            @Override
            public void onClick(WMSweetAlertDialog sDialog) {
                sDialog.dismissWithAnimation();
            }
        })
        .show();


Disable button

    final WMSweetAlertDialog disabledBtnDialog = new WMSweetAlertDialog(this, WMSweetAlertDialog.NORMAL_TYPE)
            .setTitleText("Title")
            .setContentText("Disabled button dialog")
            .setConfirmText("Confirm")
            .setCancelText("Cancel")

    disabledBtnDialog.setOnShowListener(new DialogInterface.OnShowListener() {
        @Override
        public void onShow(DialogInterface dialog) {
            disabledBtnDialog.getButton(WMSweetAlertDialog.BUTTON_CONFIRM).setEnabled(false);
        }
    });
    disabledBtnDialog.show();


**Change** the dialog style upon confirming：

    new WMSweetAlertDialog(this, WMSweetAlertDialog.WARNING_TYPE)
        .setTitleText("Are you sure?")
        .setContentText("Won't be able to recover this file!")
        .setConfirmText("Yes,delete it!")
        .setConfirmClickListener(new WMSweetAlertDialog.OnSweetClickListener() {
            @Override
            public void onClick(WMSweetAlertDialog sDialog) {
                sDialog
                    .setTitleText("Deleted!")
                    .setContentText("Your imaginary file has been deleted!")
                    .setConfirmText("OK")
                    .setConfirmClickListener(null)
                    .changeAlertType(WMSweetAlertDialog.SUCCESS_TYPE);
            }
        })
        .show();


## License

    The MIT License (MIT)

    Copyright (c) 2014 Pedant(http://pedant.cn)

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.


