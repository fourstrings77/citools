ARG PHPVERSION="8.2"


FROM php:${PHPVERSION}-cli-alpine

RUN apk add --no-cache git unzip

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /app

RUN composer global require \
    squizlabs/php_codesniffer \
    phpstan/phpstan \
    phpunit/phpunit \
    --prefer-dist --no-interaction --no-progress --optimize-autoloader

ENV PATH="/root/.composer/vendor/bin:${PATH}"

# Optional: Standardbefehl definieren, wenn das Image ohne Befehl ausgeführt wird
# Das ist nützlich, wenn man das Image interaktiv nutzen will, aber nicht zwingend für CI/CD.
# ENTRYPOINT ["php"]
# CMD ["--version"]