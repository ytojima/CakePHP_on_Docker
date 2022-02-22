FROM php:7.4.28-apache

# コンテナのアップデートと必要ライブラリのインストール
RUN apt -y update && \
    apt -y upgrade && \
    apt -y install  \
            git \
            libicu-dev \
            unzip \
            zip

# Composerをマルチステージビルド
COPY --from=composer /usr/bin/composer /usr/bin/composer

# CakePHP v3に必要なPHPライブラリ
RUN docker-php-ext-install intl pdo_mysql

# mod_rewiteの有効化
RUN a2enmod rewrite

# 作業ディレクトリの指定
WORKDIR /var/www/html
