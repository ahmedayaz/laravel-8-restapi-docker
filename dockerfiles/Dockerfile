FROM php:8.2.1-cli-alpine

# Linux Library and PHP Extentions required for Laravel
# RUN apt-get update && apt-get install -y \
# 		libfreetype-dev \
# 		libjpeg62-turbo-dev \



# 	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
# 	&& docker-php-ext-install -j$(nproc)   pdo  \
#     && docker-php-ext-enable 

RUN apk --no-cache add git curl freetype-dev libjpeg-turbo-dev libpng-dev libxml2-dev zip unzip nodejs npm libzip-dev zip oniguruma-dev icu-dev
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-configure intl
# Install PHP extensions
RUN docker-php-ext-install -j$(nproc) pdo pdo_mysql intl mbstring exif pcntl bcmath gd zip	mysqli
	
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN chown -R www-data:www-data /var/www/html

# Set working directory
WORKDIR /var/www/html

# Copy project files
COPY . .

EXPOSE 8000


CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]