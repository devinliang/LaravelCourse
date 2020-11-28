# LaravelCourse

## Requirements 安裝前需求

  - PHP >= 7.3
  - Composer 
  - Node JS with npm
  
## Composer 升級

    composer self-update
  
## Laravel 安裝

  - 方法一
  
    composer global require laravel/installer

自動安裝最新版

    laravel new 專案名稱

  - 方法二

    composer create-project --prefer-dist laravel/laravel 專案名稱

安裝各種不同版本

    composer create-project --prefer-dist laravel/laravel=7.* 專案名稱

## 執行 Laravel

    cd 專案名稱folder
    php artisan serve
