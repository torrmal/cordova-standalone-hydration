cordova-standalone-hydration
============================

This is a standalone hydration (app updater) script.

Simply call AppUpdater with the url containing a json file describing the contents of your app.

Example:

```

document.addEventListener(
                'deviceready', 
                function(){
                    AppUpdater('http://localhost:3000/mobile_app/app_info');
                }, 
                false
            ); 

```

In this case http://localhost:3000/mobile_app/app_info returns following JSON:

```
{
	"base_url":"http://localhost:3000/mobile_app",
	"files":[
		"/index.html",
		"/images/logo.png"
	]
}
```

Where 
- base_url: is the url where the app to be downlaoded is located at
- file: a list of files to download from the base_url (pretty much a list of all the files in your app). Use a script to generate this JSON.

In summary your ohonegap index.html should look something like this:



<html>
   
    <body>
       
        <script type="text/javascript" src="cordova.js"></script>
        
        
        <script type="text/javascript" src="AppUpdater.js"></script>
        <script type="text/javascript">
           

            document.addEventListener(
                'deviceready', 
                function(){
                    AppUpdater('http://localhost:3000/mobile_app/app_info');
                }, 
                false
            );

             

        </script>
    </body>
</html>

