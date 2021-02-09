# Pinview

[![](https://jitpack.io/v/skree-tech/Pinview.svg)](https://jitpack.io/#skree-tech/Pinview)


## Gradle Dependency

Add this in your root build.gradle file at the end of repositories:
```java
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```
Add the dependency : 
```java
dependencies {

	        implementation 'com.github.skree-tech:Pinview:Tag'

	}
```
Sync the gradle and that's it! :+1:

### Features : 
 * Flawless focus change to the consecutive pin box when the text is entered/deleted.
 * When the user taps on the Pinview, the first empty box available is focused automatically (when the cursor is hidden).
 * Listeners for onDataEntered ( To call an API when the pin is entered) and touch exists.
 * Customisations are available for pin box sizes, background(drawables, selectors), inputType , hintTextColors, etc.
 
## Usage

### XML : 
```xml
<com.goodiebag.pinview.Pinview
        android:id="@+id/pinview"
        app:pinBackground="@drawable/example_drawable"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:pinWidth="40dp"
        app:pinHeight="40dp"
        app:pinLength="4"
        app:cursorVisible="false"
	app:forceKeyboard="true"
        app:hint="0"
        app:inputType="text"
        app:password="false"/>
```
This can be referenced in the java class by the ```findViewById``` method.

##### Available xml attributes and explanations : 

```app:pinBackground``` : Sets the pin box's background, accepts a drawable or a selector drawable. When a ```selector``` is used, the focused pin box is highlighted. <br />
```app:pinWidth``` and ```app:pinHeight``` : Sets the width and height of the pinbox. <br />
```app:pinLength``` : number of pin boxes to be displayed.<br />
```app:forceKeyboard``` : forces the keyboard when the pinview is activity/fragment is opened.
```app:cursorVisibility``` : Toggles cursor visibility.<br />
```app:hint``` : Pin box hint. <br />
```app:inputType``` : Accepts ```number``` or ```text``` as values. <br />
```app:password``` : Masks the pin value with ```*``` when true. <br />
```app:splitWidth``` : Determines the width between two pin boxes.

### Java : 

To create the view programmatically : 
```java
Pinview pin = new Pinview(this);
```
Or reference it from findViewById
```java
pin = (Pinview) findViewById(R.id.pinview);
pin.setPinBackgroundRes(R.drawable.sample_background);
pin.setPinHeight(40);
pin.setPinWidth(40);
pin.setInputType(Pinview.InputType.NUMBER);
pin.setValue("1234");
pin.setTextColor(Color.WHITE);


pin.setTextHintColor(Color.GRAY);
myLayout.addView(pin);    
```
##### To get and set the pin values use the ```pin.getValue()``` and ```pin.setValue()``` methods respectively.

There is an event listener which is triggered when the user is done entering the otp which can be used as follows : 
```java
pinview.setPinViewEventListener(new Pinview.PinViewEventListener() {
            @Override
            public void onDataEntered(Pinview pinview, boolean fromUser) {
	    	//Make api calls here or what not
                Toast.makeText(MainActivity.this, pinview.getValue(), Toast.LENGTH_SHORT).show();
            }
        });
```
#### Note : 
This library cannot be assured to work on 3rd party keyboards (especially when the cursor is off). It works as expected on google keyboards.
We will be adding a work-around in the future releases.


