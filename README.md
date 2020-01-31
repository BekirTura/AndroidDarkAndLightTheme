# AndroidDarkAndLightTheme
Android Dark Mode , Light Mode

# Change Theme With Single Line Code

```Java
getDelegate().setLocalNightMode(AppCompatDelegate.MODE_NIGHT_YES);
```

* First Step

```
res/ Dicrectory Add values-night directory

```

* Seconds Step

```
values-night directory add colors.xml file 
```

* colors.xml

```xml-in 
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="colorPrimary">#008577</color>
    <color name="colorPrimaryDark">#00574B</color>
    <color name="colorAccent">#D81B60</color>
    <color name="textColorPrimary">#000000</color>
    <color name="colorBackground">#FFFFFF</color>
</resources>

```

* colors.xml (night)


```xml-in 
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="colorPrimary">#3F51B5</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="textColorPrimary">#FFFFFF</color>
    <color name="colorBackground">#000000</color>
</resources>

```
# Third Step

* Layout

    android:background="@color/colorBackground"
    android:background="@color/colorBackground"


```xml-in 
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/colorBackground"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/text"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textColor="@color/textColorPrimary"
        android:layout_centerInParent="true"/>



    <Button
        android:layout_below="@+id/text"
        android:id="@+id/button_change_theme"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/button_change_theme_board" />

</RelativeLayout>


```
# Fourth Step

Theme Change Mode Code 

Dark Mode On = getDelegate().setLocalNightMode(AppCompatDelegate.MODE_NIGHT_YES);

Light Mode On = getDelegate().setLocalNightMode(AppCompatDelegate.MODE_NIGHT_NO);



* Main Activity

```Java 
public class MainActivity extends AppCompatActivity {

    Button btnChangeTheme;

    boolean themeLight = true;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        btnChangeTheme = findViewById(R.id.button_change_theme);

        btnChangeTheme.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if(themeLight){
                    themeLight = false;
                    getDelegate().setLocalNightMode(AppCompatDelegate.MODE_NIGHT_YES);
                }else{
                    themeLight = true;
                    getDelegate().setLocalNightMode(AppCompatDelegate.MODE_NIGHT_NO);
                }
            }
        });
    }
}


```

# Requirements
* App/Build.Gradle

```Groovy 
apply plugin: 'com.android.application'

android {
    compileSdkVersion 29
    buildToolsVersion "29.0.2"
    defaultConfig {
        applicationId "com.bekirtura.androidlightdarkthemeapp"
        minSdkVersion 19
        targetSdkVersion 29
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
    }
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation 'androidx.appcompat:appcompat:1.1.0'
    implementation 'androidx.constraintlayout:constraintlayout:1.1.3'
    testImplementation 'junit:junit:4.12'
    androidTestImplementation 'androidx.test.ext:junit:1.1.1'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.2.0'
}


```
