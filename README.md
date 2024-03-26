# CMD
### Create new project
- composer create-project laravel/laravel:^10 namaProject

### Local Development Server
- php artisan serve

### File .env
- DB_DATABASE = 'NAMA_DATABASE'
- DB_USERNAME = 'root'
- DB_PASSWORD = ''

### Migration
- php artisan make:migration create_users_table, users -> nama tabelnya
- 
# Routing
### simple routing
```
Route::get('/greeting', function(){return 'hello world'})
```
### default page when run LDS
```
Route::get('/', function () {
    return view('dashboard', ['name' => ['Vincent','Hadinata']]);
});
```
### routing with parameter
```
Route::get('/namaDirektori/{parameter}', function($parameter){
    return 'hello '.$parameter
});
```
# Sintaks
```
  @if (count($record) === 1)
      I have one record!
  @elseif (count($record) > 2)
      I have multiple records!
  @else
      I don't have records !
  @endif
```
```
  @foreach ($queryModel as $data)
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
```
# Migration
### Creating table
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::create('hotels', function (Blueprint $table) {
            $table->id();
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::dropIfExists('hotels');
    }
};
```
### Adding columns
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::table('hotels', function (Blueprint $table) {
            //
            $table->string('name',100);
            $table->string('address',100);
            $table->integer('postcode');
            $table->string('city',100);
            $table->string('state',100);
            $table->integer('country_id');
            $table->double('longitude');
            $table->double('latitude');
            $table->Integer('phone');
            $table->string('fax');
            $table->string('email');
            $table->string('currency');
            $table->string('accomodation_type');
            $table->string('category');
            $table->string('web');
        });
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::table('hotels', function (Blueprint $table) {
            //
            $table->dropColumns('name');
            $table->dropColumns('address');
            $table->dropColumns('postcode');
            $table->dropColumns('city');
            $table->dropColumns('state');
            $table->dropColumns('country_id');
            $table->dropColumns('longitude');
            $table->dropColumns('latitude');
            $table->dropColumns('phone');
            $table->dropColumns('fax');
            $table->dropColumns('email');
            $table->dropColumns('currency');
            $table->dropColumns('accomodation_type');
            $table->dropColumns('accomodation_type');
            $table->dropColumns('category');
            $table->dropColumns('web');
        });
    }
};
```
### Add foreign key
```
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::table('products', function (Blueprint $table) {
            //
            $table->unsignedBigInteger('hotel_id');
            $table->foreign('hotel_id')->references('id')->on('hotels');
        });
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::table('products', function (Blueprint $table) {
            //
            $table->dropForeign('hotel_id');
            $table->dropColumn('hotel_id');
        });
    }
};
```
