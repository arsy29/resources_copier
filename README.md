This assums you are using npm, node and cordova-cli.
```bash
npm install cordova
```

Install
-------

Copy `resources_copier.js` into the `.cordova/hooks/before_prepare` directory.

Assets directory
----------------

Create a `config` folder on the root of your cordova project. Place your assets (icons & splash screens) in that directory;
```text
.cordova
config
`-- android
    |-- res
    |   |-- drawable
    |       |-- icon.png
    |       `-- splash.png
    |   |-- drawable-hdpi
    |       |-- icon.png
    |       `-- splash.png
    |   |-- drawable-land-hdpi
    |       |-- icon.png
    |       `-- splash.png
    |   |-- ...
platforms
www
...
```

Test
----
Type in the CLI `cordova prepare android`. It copies files into the Android platforms. To debug add -d; `cordova prepare android -d`

You may have to user `sudo chmod -R a+rwx ./.cordova/hooks/before_prepare/resources_copier.js` to update permissions to run the hook.

Usage and platform notes
------------------------
### Android splash screen

In order to take advantage of the splash screen in Android, add this two linees to the `config.xml` in your `www` folder

```xml
<preference name="SplashScreen" value="splash" />
<preference name="SplashScreenDelay" value="3000" />
```
#### Notes

As of cordova 3.3 and Android splash screen support; cordova assums you put landscape screens in folders where you append `land` to the name, like; `drawable-land-xhdpi`
