# Langlocale App to Laravel 5

## Installation

**1 - After install Laravel framework, insert on file composer.json, inside require object this value**
```
"syscover/langlocale": "dev-master"

```

**2 - Register service provider, on file config/app.php add to providers array**

```
'Syscover\Langlocale\LanglocaleServiceProvider',

```

**3 - Register middlewares langlocale.pulsar on file app/Http/Kernel.php add to routeMiddleware array**

```
'langlocale.pulsar' => 'Syscover\Langlocale\Middleware\SetLangLocaleUser',

```

**4 - To publish package, you must type on console**

```
php artisan vendor:publish --force

```

**5 - Set config options on config\langlocale.php**

**6 - on app\Http\routes.php file use this cloure to implement routes with translation**

```
Route::group(['middleware' => ['langlocale.pulsar']], function() {

    // write here your routes

});

```

**7 - Route configutation**
you have several configuration options:

Write your routes with locale variable:

```
Route::group(['middleware' => ['langlocale.pulsar']], function() {
    Route::get('/',                         function(){ return view('www.index'); });
    Route::get('{locale}',                  function(){ return view('www.index'); });
    Route::post('{locale}/contact',         ['as'=>'contact',  'uses'=>'FrontEndController@contact']);
});

```

Set lang variable on your routes

```
Route::group(['middleware' => ['langlocale.pulsar']], function() {
    Route::get('/',                   function(){ return view('www.index'); });

    Route::get('en',                  function(){ return view('www.index'); });
    Route::get('es',                  function(){ return view('www.index'); });

    Route::post('en/contact',         ['as'=>'contact',          'uses'=>'FrontEndController@contact']);
    Route::post('es/contacto',        ['as'=>'contact',          'uses'=>'FrontEndController@contact']);
});

```
