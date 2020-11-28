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
    
## 路由參數

  - students/學號
  - students/學號/score/
  - students/學號/score/科目
    
可以分別由以下方式設定:

    Route::get('students/{sno}', function($sno) {
        return '學號:'. $no;
    });
    
    Route::get('students/{sno}/score', function($sno) {
        return '學號:'. $no . '的所有成績';
    });
    
    Route::get('students/{sno}/score/{subj}', function($sno, $subj) {
        return '學號:'. $no . '的'. $subj . '成績';
    });
    
參數可加入預設值:

  1. 加上問號?表示參數可有可無
  
  - students/[學號]/score/[科目?]

  2. 使用 is_null 判斷參數是否存在

    Route::get('students/{sno}/score/{subj?}',
        function($sno, $subj=null) {
            return '學號:'. $no . '的'. ((is_null($subj) ? '所有科目' : $subj) . '成績';
        }
    );
    
參數可以使用正規表達式(Regular Expression):

  - 學號以大寫 S 開頭及10個數字組成
  - 科目有 chinese, english, math 三個科目

使用 where 設定規則式:

    Route::get('students/{sno}', function($sno) {
            return '學號:'. $no;
    }) -> where(['sno' => 'S[0-9]{10}']);
   
    Route::get('students/{sno}/score/{subj?}',
        function($sno, $subj=null) {
            return '學號:'. $no . '的'. ((is_null($subj) ? '所有科目' : $subj) . '成績';
        }
    ) -> where(['sno' => 'S[0-9]{10}','subj'=>'(chinese|english|math)']);

參數可以用 Route 的 pattern 設定統一格式:

    Route::pattern('sno', 'S[0-9]{10}');
    Route::pattern('subj', '(chinese|english|math)');
    
    Route::get('students/{sno}', function($sno) {
            return '學號:'. $no;
    });
   
    Route::get('students/{sno}/score/{subj?}',
        function($sno, $subj=null) {
            return '學號:'. $no . '的'. ((is_null($subj) ? '所有科目' : $subj) . '成績';
        }
    );

## 路由群組

## 路由命名

## 查看路由表

    php artisan route:list
    
可簡寫為:

    php artisan r:l
