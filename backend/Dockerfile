# PHPとComposerが含まれるイメージをベースにする
FROM php:8.1-fpm

# Composerをインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# 必要なPHP拡張機能をインストール
RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    && docker-php-ext-install zip pdo_mysql

# Laravelの設定と依存関係のインストール
WORKDIR /app

# アプリケーションのソースコードをコピー
COPY . /app

# .envを作成
RUN cp .env.example .env

# Composerを使って依存関係をインストール
RUN composer install --no-interaction --optimize-autoloader --no-dev

# Laravelのストレージとキャッシュディレクトリの権限を設定
RUN chown -R www-data:www-data /app/storage /app/bootstrap/cache

# コンテナ起動時に実行されるコマンド
CMD ["php-fpm"]
