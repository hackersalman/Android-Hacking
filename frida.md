## Hooking Activity

**Steps**

    Terminal: 1
    1. adb shell
    2. su
    3. cd /data/local/tmp
    4. ./frida-server-17.4.1-android-x86_64
    
    Terminal: 2
    1. Run app in background.
    2. adb shell pm list packages -U | grep -i <package-name>
    3. adb shell ps -A | grep -i <package-name> >> To see the `PID` of the apk/package
    4. frida -U -p <PID> >> To hook the apk via pid 
    5. Now paste hook.js and enter
    
    Mobile:
    1. Press ⚪ Home
    2. Press ⬜ Recent Apps
    3. Open target app.

hook.js
```
Java.perform(function() {
  const Activity = Java.use('android.app.Activity');
  Activity.onResume.implementation = function () {
    send('onResume() got called! Let\'s call the original implementation');
    this.onResume();
  };
});
```

