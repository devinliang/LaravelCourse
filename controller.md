## Controller 

建立 Controller

    php artisan make:controller HomeController

執行之後, 在 app/Http/Controllers 底下可以看到: HomeController.php

    <?php

    namespace App\Http\Controllers;

    use Illuminate\Http\Request;

    class HomeController extends Controller
    {
       //
    }

在 HomeController 寫入以下方法:

    public function index() {
        return view('welcome');
    }

在 routes/web.php 加入以下方法:

   use App\Http\Controller;
   
   Route::get('/', 'HomeController@index');
