# PHPとComposerが含まれるイメージをベースにする
FROM composer:2 as composer
FROM php:8.1-fpm

# Composerをコピー
COPY --from=composer /usr/bin/composer /usr/bin/composer

# Laravelの設定と依存関係のインストール
WORKDIR /app
COPY . .
RUN composer install

# Laravelのストレージとキャッシュディレクトリの権限を設定
RUN chown -R www-data:www-data /app/storage /app/bootstrap/cache

# PHP-FPMを起動
CMD php artisan serve --host=0.0.0.0 --port=8000
EXPOSE 8000
