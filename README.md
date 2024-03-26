# CMD
### Create new project
- composer create-project laravel/laravel:^10 namaProject

### Local Development Server
- php artisan serve

### 

# Routing
### simple routing
- Route::get('/greeting', function(){return 'hello world'})
- 
### default page when run LDS
- Route::get('/', function () {
    return view('dashboard', ['name' => ['Vincent','Hadinata']]);
});

### routing with parameter
- ROute::get('/namaDirektori/{parameter}', function($parameter){return 'hello '.$parameter});

#Sintaks
- @if (count($record) === 1)
      I have one record!
  @elseif (count($record) > 2)
      I have multiple records!
  @else
      I don't have records !
  @endif
- @foreach ($queryModel as $data)
      <tr>
        <td>{{$data ->id}}</td>
        <td>{{$data ->created_at}}</td>
        <td>{{$data ->updated_at}}</td>
        <td>{{$data ->name}}</td>
        <td>{{$data ->price}}</td>
        <td>{{$data ->hotel_id}}</td>
        <td>{{$data ->hotels->name}}</td>
      </tr>
      @endforeach  
