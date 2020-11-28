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

## Resource

一次建立 Controller 的七大動作:

  - index 顯示所有項目
  - create 建立
  - store  儲存
  - show  顯示單筆項目
  - edit  編輯
  - update  更新
  - destroy 剛除
  
方法如下:

    php artisan make:controller UserController --reource
    
在 route/web.php 裡面, 不必個別建立route, 使用以下方法:

    use App\Http\Controller;
    Route::resource('user', 'UserController');
