#Flask on Google App Engine Template

Kelp https://twitter.com/kelp404  
[MIT License][mit]  
[MIT]: http://www.opensource.org/licenses/mit-license.php

```
   ______   __         ______     ______     __  __
  /\  ___\ /\ \       /\  __ \   /\  ___\   /\ \/ /
  \ \  __\ \ \ \____  \ \  __ \  \ \___  \  \ \  _"-.
   \ \_\    \ \_____\  \ \_\ \_\  \/\_____\  \ \_\ \_\
    \/_/     \/_____/   \/_/\/_/   \/_____/   \/_/\/_/
```

This project is my <a href="https://developers.google.com/appengine/" target="_blank">GAE</a> project template.  
And the example application uses <a href="http://www.whatwg.org/specs/web-apps/current-work/#history-0" target="_blank">History</a> to link pages, so that all hyperlinks are ajax.  




##Frameworks
+ Flask 0.9
+ Jinja 2.7
+ Werkzeug 0.8.3
+ Bootstrap 2.3.2
+ jQuery 2.0.0
+ Google App Engine Launcher 1.8.1




##How to use?
```
git clone --recursive git://github.com/kelp404/Flask-GAE.git
```

./
```
├─ application       # Web application code
├─ flask             # Flask framework
├─ jinja2            # Jinja framework
├─ tests             # Unit tests
├─ werkzeug          # Werkzeug framework
├─ app.yaml          # GAE app config
├─ backends.yaml     # GAE backends config
├─ cron_jobs.py      # Cron jobs code
├─ cron.yaml         # GAE Cron jobs config
├─ itsdangerous.py
└─ index.yaml        # GAE datasotre indexes config
```

./application/
```
├─ data_models       # Datastore data model
├─ handlers          # Web handlers (MVC's controller)
├─ models            # Other models
├─ services          # All business logic here (MVC's model)
├─ static
│  ├─ coffeescript   # CoffeeScript
│  ├─ css
│  ├─ font
│  ├─ icon
│  ├─ img
│  ├─ javascript
│  ├─ binding.py     # JavaScript, CSS binder
│  └─ robots.txt
├─ templates         # Jinja templates (MVC's view)
├─ utilities         # Web application's shared utilities(helpers)
├─ __init__.py
├─ config.py         # Application config
└─ routes.py         # Web application's routers
```




##Example application
Board: https://flask-gae-kelp.appspot.com/posts  
Chat: https://flask-gae-kelp.appspot.com/chat  




##Deploy with <a href="https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python" target="_blank">appcfg.py</a>
You should create a GAE account.  
https://appengine.google.com  
  
###update `app.yaml`
```Python
application: flask-gae-kelp
'flask-gae-kelp' should replace to your Application Identifier.
```

###deploy project
**deploy**
```Python
appcfg.py update Flask-GAE/
* Flask-GAE is the folder name of the project
```
**deploy backends**
```
appcfg.py backends Flask-GAE/ update
```

###deleting unused indexes
```
appcfg.py vacuum_indexes myapp/
# https://developers.google.com/appengine/docs/python/tools/uploadinganapp?hl=en#Deleting_Unused_Indexes
```




##<a href="https://github.com/chriseppstein/compass" target="_blank">Compass</a>
###PyCharm settings
`File Watchers` >> add `SCSS`

  Watcher Settings  |  value 
:---------:|:---------:
Program | /Users/Kelp/.rvm/gems/ruby-1.9.3-p392/bin/compass
Arguments | compile
Environment variables | GEM_PATH: `/Users/Kelp/.rvm/gems/ruby-1.9.3-p392`
Output paths | $FileNameWithoutExtension$.css




##Compress
###PyCharm settings
Add the plugin "Assets Compressor".
> Compressing js and css files, go to Refactor > Compress




##Binding JavaScript, CSS
```
$ cd application/static
$ python binding.py
```




##Unittest
Before test, you should run GAE local server, and clear datastore, text search, and update url in function 'setUp()'.
```Python
class TestFunctions(unittest.TestCase):
    def setUp(self):
        self.url = 'http://localhost:8081'
        self.email = 'kelp@phate.org'
        self.cookies = { 'dev_appserver_login': "kelp@phate.org:True:111325016121394242422" }
```
clear datastore & text search:
```
--clear_datastore=yes --clear_search_indexes=yes
```
```
$ cd Flask-GAE
$ python tests
```
Python unit test reference: <a href="http://docs.python.org/2/library/unittest.html" target="_blank">http://docs.python.org/2/library/unittest.html</a>



##References
+ <a href="https://developers.google.com/appengine/downloads" target="_blank">Google App Engine SDK</a>
+ <a href="https://developers.google.com/appengine/docs/python/overview" target="_blank">Google App Engine Python Overview</a>
+ <a href="https://github.com/mitsuhiko/flask" target="_blank">Flask on GitHub</a>
(<a href="http://flask.pocoo.org/" target="_blank">document</a>)
+ <a href="https://github.com/mitsuhiko/jinja2" target="_blank">Jinja2 on GitHub</a>
(<a href="http://jinja.pocoo.org/" target="_blank">document</a>)
+ <a href="https://github.com/mitsuhiko/werkzeug" target="_blank">Werkzeug on GitHub</a>
(<a href="http://werkzeug.pocoo.org/" target="_blank">document</a>)
+ <a href="https://github.com/mitsuhiko/itsdangerous" target="_blank">itsdangerous on GitHub</a>
+ <a href="http://twitter.github.com/bootstrap/" target="_blank">Bootstrap</a>
+ <a href="https://github.com/jashkenas/coffee-script" target="_blank">CoffeeScript on GitHub</a>
(<a href="http://coffeescript.org/" target="_blank">document</a>)
+ <a href="http://jquery.com/" target="_blank">jQuery</a>
+ <a href="https://github.com/kennethreitz/requests" target="_blank">Requests on GitHub</a>
+ <a href="http://www.crummy.com/software/BeautifulSoup/bs4/doc/" target="_blank">Beautiful Soup</a>
+ <a href="https://github.com/chriseppstein/compass" target="_blank">Compass on GitHub</a>
+ <a href="https://github.com/thomas-mcdonald/bootstrap-sass" target="_blank">Bootstrap for Sass on GitHub</a>
