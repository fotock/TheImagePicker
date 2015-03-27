# TheImagePicker
Android library project for multiple image selection.
Based on PolyPicker.

Features
==========
* Multi-selection of images from gallery.
* Taking pictures from camera.
* Autofocus.
* Select/capture images upto a specified limit.
* Preview thumbnails of selected images.

Download
==========
```groovy

dependencies {
    compile 'com.sanfriend:theimagepicker:1.0.4@aar'
}

```
Requires Android 4.0+.

Getting started
==========

A. AndroidManifest.xml

```xml
<uses-feature android:name="android.hardware.camera" />
<uses-feature android:name="android.hardware.camera.autofocus" />

<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

B. Declare TheImagePicker activity in your AndroidManifest.xml

```xml

<activity
    android:name="com.sanfriend.theimagepicker.TheImagePickerActivity"
    android:theme="@android:style/Theme.Holo" />
    
```

C. Request large heap memory using "largeHeap" attribute for your application. This will avoid application to
crash on low memory devices. The side effect would be that your application may force
other applications to be kicked out of memory. Nothing very severe.

```xml

<application
        android:icon="@drawable/ic_launcher"
        android:label="@string/app_name"
        android:largeHeap="true">
        .
        .
</application>

```

``

Start TheImagePicker activity and get the result back.

```java

private void getImages() {
    Intent intent = new Intent(mContext, TheImagePickerActivity.class);
    intent.putExtra(TheImagePickerActivity.EXTRA_SELECTION_LIMIT, 6);  // upto 6 images could be selected.
    startActivityForResult(intent, INTENT_REQUEST_GET_IMAGES);
}

@Override
protected void onActivityResult(int requestCode, int resultCode, Intent intent) {
    super.onActivityResult(requestCode, resultCode, intent);

    if (resultCode == Activity.RESULT_OK) {
        if (requestCode == INTENT_REQUEST_GET_IMAGES) {
            Parcelable[] parcelableUris = intent.getParcelableArrayExtra(TheImagePickerActivity.EXTRA_IMAGE_URIS);

            if(parcelableUris == null) {
                return;
            }

            //...
        }
    }
}

```

Contributing
==============

Please fork this repository and contribute back using
[pull requests](https://github.com/fotock/TheImagePicker/pulls).

Please follow Android code [style guide](https://source.android.com/source/code-style.html)

## You can contribute in following ways
 * Test on multiple devices you have
 * Write unit tests
 * Help with string translations
 * Fix open issues in the library

Developed by
============
 * Shelley Shyan - <shelleyshyan@gmail.com>


Alternative projects
==========
* [poly-picker](https://github.com/jaydeepw/poly-picker)
* [android-multiple-image-picker](https://github.com/giljulio/android-multiple-image-picker)
* [MultipleImagePick](https://github.com/luminousman/MultipleImagePick)

