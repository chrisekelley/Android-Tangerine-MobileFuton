## Welcome!

This is a demonstration of using Dale Harvey's [Mobile Futon](https://github.com/daleharvey/Android-MobileFuton) as a platform for other apps. 

## Packaging the app

My app is targeting Android 2.1-update 1 (API level 7) which is used on the Nexus One. 
This version has a limit of 1MB for files in the assets directory. 
The workaround is to rename any files over 1 MB with an extention that is one of the formats that is not uncompressed by default Android. 
See [Dealing with Asset Compression in Android Apps](http://ponystyle.com/blog/2010/03/26/dealing-with-asset-compression-in-android-apps/) for more info.
Note - this is no longer an issue w/ Android 2.3.

    couchapp push --export > ../Android-Tangerine-MobileFuton/assets/egra.json.jpg
    
## Installing the app

Here is the code from [MobileFutonActivity](https://github.com/vetula/Android-Tangerine-MobileFuton/blob/master/src/com/daleharvey/mobilefuton/MobileFutonActivity.java) that installs the couchapps and launches my app instead of Mobile Futon:

    ensureLoadDoc("mobilefuton", url, "_design/mobilefuton", "mobilefuton.json");
	ensureLoadDoc("egra", url, "_design/app", "egra.json.jpg");
	launchFuton(url + "egra/_design/app/index.html" + param);
    
I made some minor changes to Dale Harvey's code to load non-designDocs.