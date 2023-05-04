FROM php:7.4-cli 

WORKDIR /var/www

RUN echo '## Atualizando Linux e instalando pacote zip e extensão zip para o php ##'
RUN apt-get update && \
    apt-get install libzip-dev -y && \
    docker-php-ext-install zip

RUN echo '## Instalando composer ##' 
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php &&\
    php -r "unlink('composer-setup.php');"

RUN echo '## Criando projeto laravel ##'
RUN php composer.phar create-project --prefer-dist laravel/laravel laravel

RUN echo '## Rodando artisan serve ##'
ENTRYPOINT [ "php","laravel/artisan","serve" ]

CMD [ "--host=0.0.0.0" ]