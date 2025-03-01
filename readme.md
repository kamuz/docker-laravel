# Setup Docker for Laravel projects

Clone repo and build/run Docker:

```
git clone git@github.com:kamuz/docker-laravel.git
git clone https://github.com/laravel/laravel.git laravel
cp -rf docker-laravel/* laravel/
cd laravel/
cp env.example .env
docker-compose up -d
docker-compose exec app bash
```

Install dependencies and generate `APP_KEY`:

```
composer install
php artisan key:generate
```

Check Laravel - [http://localhost:8888/](http://localhost:8888/)

Check phpMyAdmin (`laravel/laravel`) - [http://localhost:8080/](http://localhost:8080/)

Run migrations:

```
php artisan migrate
```

Test email with Tinker:

```
php artisan tinker
```

Send email:

```
use Illuminate\Support\Facades\Mail;

Mail::raw('This is a test email', function ($message) {
    $message->to('recipient@example.com')
            ->subject('Test Email')
            ->from('your-email@example.com');
});
```

Check Email - [http://localhost:8025/](http://localhost:8025/)