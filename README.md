# CMD
### Create new project
- composer create-project laravel/laravel:^10 namaProject

### Local Development Server
- php artisan serve

#Routing
### simple routing
- Route::get('/greeting', function(){return 'hello world'})
### default page when run LDS
- Route::get('/', function () {
    return view('dashboard', ['name' => ['Vincent','Hadinata']]);
});
