# Laravel

## Laravel

![Larabel](readme_assets/Untitled.png)

라라벨은 php 에서 주로 사용하는 웹 프레임워크.

Taylor Otwell과 커뮤니티 회원들에 의해 개발되었고 php의 기능을 최대한 활용하되 코드를 손쉽게 작성할 수 있도록 사용이 쉬운 기능을 제공하고 약간의 코딩으로 강력한 기능을 만들 수 있도록 개발되었다.

오른쪽 구글 트렌드에서와 같이 다른 프레임워크와 달리 빠른 성장세와 압도적 점유율을 보이고 있고 레일즈나 장고 못지 않은 인기를 누리고 있다.

라라벨의 장점은 MVC 패턴을 지원하고 20가지 이상의 웹 개발에 필요한 객체지향 라이브러리를 제공받고 명령 줄 인터페이스를 통한 유지 관리가 가능하도록 돕다.

또한 편리한 템플릿 엔진과 효율적인 ORM을 통한 데이터베이스 관리, 효과적인 단위 테스트 지원 등 많ㅇ느 장점들이 모여 있는 프레임워크다.

![google trend for php framework](readme_assets/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-21_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_10.17.37.png)

## PHP

![php](readme_assets/Untitled%201.png)

PHP(Hypertext Preprocessor)는 동적 웹 페이지를 만들기 위해 설계된 프로그래밍 언어의 일종.

php로 작성된 코드를 html 소스 문서안에 넣으면 php처리기능이 있는 웹 서버에서 코드를 인식해 웹 페이지를 생성하는 방식으로 동작한다.

php의 특징은 웹개발에 특화된 언어이고 C언어 기반의 언어이며 스크립트 언어이다.

서버 쪽 지원이 부족한 언어로서 언어 커뮤니티 인덱스에서 보듯이2004년에 전성기를 누리고 하락세이기는 하지만 Laravel 이 성장함에 따라 사용성이 많이 개선된 언어이기도 하다.

![tiobe programming community index](readme_assets/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-03-21_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_10.09.29.png)

## INSTALLATION

### Install PHP

```bash
brew install php
brew services start php
```

### Composer

- Dependency Manager for PHP
- Install Composer

```bash
sudo curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/
sudo ln -s /usr/local/bin/composer.phar /usr/local/bin/composer
```

### Get Started Laravel Project

```bash
# laravel project start with composer
composer create-project --prefer-dist laravel/laravel laravel-app
```

### Swoole - Laravel/Octane

- Swoole 은 php extension 으로서 PHP CORE 를 확장해 더 많은 기능을 제공하도록 돕고 대규모 동시 처리 시스템 구축을 위해 설계됐는데 앱을 한 번 로드하고 메모리에 보관해 각 요청에 대해 앱을 부팅하지 않고도 모든 요청을 처리하도록 합니다. Laravle/Octane 을 활용해 사용할 수 있습니다.
- Octane 은 성능을 향상시키면서 앱을 쉽게 제공할 수 있게 돕는 laravel 의 first-party 라이브러리이다. 이전에는 Nginx + PHP-FPM 조합으로 모든 요청에 대해 프로세스를 생성하고 Laravel 앱을 처음부터 부팅해하는 처리를 하는 비효율적 프로세스가 필요했지만 Octane 을 활용하면 앱을 한번 로드하고 메모리에 유지해 모든 요청을 처리하는 방식이다. Octane 에서 이를 위해 RoadRunner 와 Swoole 중 하나를 사용합니다.
- RoadRunner vs Swoole
    - Swoole
        - 앱의 성능을 높이고 많은 기능을 언어에 추가하는 php 의 확장으로서 RoadRunner 보다 훨씬 더 많은 기능을 갖추고 있다.
        - concurrent tasks(동시 작업), ticks(주기 작업), octane caching(고성능 메모리 캐시), swoole tables(메모리 데이터 저장소)
        - php 의 확장이므로 빌드단계에서 컴파일해야 함. laravel sail 에는 로컬 개발을 위한 docker image 에 swoole 이 내장되어 있음.
        - Xdebug와 동작하지 않음. yasd 라는 swoole 과 동작하는 새로운 디버깅 도구가 있지만 Xdebug 만큼 성숙하지 않음.
    - RoadRunner
        - php extension 이 아님.
        - Swoole과 달리 PHP-FPM 을 대체하는 역활을 함. 언어 자체로 컴파일할 필요가 없어 배포가 더 수월함.
        - Xdebug 도구도 사용이 가능.
        - Swoole 에서 제공하는 추가 기능들, 모니터링 부족

```bash
# swoole 설치
pecl install swoole
# octane 설치
composer require laravel/octane
# 프로젝트 내 octane 설정 설치
php artisan octane:install
# development
php artisan octane:start
# or
# install watch from node chokidar
npm install --save-dev chokidar
# development with watch
php artisan octane:start --watch
# 옥탄 워커수 지정
php artisan octane:start --workers=4
# 옥탄 테스크 워커 수 지정 (swoole전용)
php artisan octane:start --workers=4 --task-workers=6
# WAS를 특정 개수 이상의 요청 후에 껐다 켜기 위해서는 다음의 명령
php artisan octane:start --max-requests=250
# 강제로 리로드
php artisan octane:reload
# 옥탄 멈춤
php artisan octane:stop
# 서버 상태확인
php artisan octane:status
```

## Dockerize & Deployment

### Sail

- Laravel 을 도커로 컴파일 하기 위한 도구
- 데이터베이스도 함께 설정이 가능
- sail 설치 시 docker-compose.yml 이 생성되고 생성된 파일을 ./vendor/bin/sail 스크립트를 통해 빌드

```bash
# sail 설치
composer require laravel/sail --dev
# 프로젝트 내 sail 설정 설치
php artisan sail:install
# docker 에 올리기
./vendor/bin/sail up
# sail 에서 otane 돌리기
./vendor/bin/sail artisan sail:publish
# 이려면, docker디렉토리가 생기고, 그것에 버전별 파일이 생성된다. 생성된 파일을 수정하여 개발서버가 아닌 옥탄이 실행되도록 한다.
command=/usr/bin/php -d variables_order=EGPCS /var/www/html/artisan octane:start --server=swoole --host=0.0.0.0 --port=80
# 그후, sail을 다시 빌드한다.
./vendor/bin/sail build --no-cache
```