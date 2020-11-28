# Route 路由控制

- 路由位置: routes/web.php

## HTTP methods

- GET
- POST
- PUT
- PATCH
- DELETE

註冊回應的方法

- Route::get($uri, $callback);
- Route::post($uri, $callback);
- Route::put($uri, $callback);
- Route::patch($uri, $callback);
- Route::delete($uri, $callback);

## 對應多個 methods

- match
- any

註冊對應的方法

    Route::match(['get', 'post'], '/',  function() {
      // 只接受 GET 和 POST 的方法, 經由路由'/'
    });
    
    Route::any('/',  function() {
      // 接受所有方法, 經由路由'/'
    });
    
