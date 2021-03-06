---
title: Composer и Packagist 
isChild: true
---

## Composer и Packagist

Composer является **блестящим** менджером зависимостей для PHP. Укажите список зависимостей вашего проекта, в файле `composer.json` и с несколькими простыми командами, Composer автоматически скачает зависимости вашего проекта и установит автозагрузку для вас. 

Уже существует много PHP библиотек, которые совместимы с Composer, готовых для использования в вашем проекте. Список этих "пакетов" есть на [Packagist][1], оффициальном репозитории для Composer-совместимых PHP библиотек. 

### Как установить Composer

Вы можете установить Composer локально(в вашей текущей рабочей директории; хотя это больше не рекомендуется) или глобально(например /usr/local/bin). Предположим вы хотите установить Composer локально. Из корневой директории вашего проекта выполните:

    curl -s http://getcomposer.org/installer | php

Это позволит загрузить файл `composer.phar` (двоичный PHP архив). Вы можете запустить его, исопльзуя `php` для управления зависимостями вашего проекта. <strong>Обратите внимание:</strong> Если вы скачаете код напрямую в ваш интерпретатор, пожалуйста, сперва прочитайте код онлайн, для потверждения его безопасности.

### Как установить Composer (вручную)

Ручная установка Composer - это продвинутая техника; однако, существуют разные причины, почему разработчик может предпочесть этот метод, использованию интерактивной установки. Интерактивная установка проверяет вашу установку PHP, чтобы подвердить, что:

- Используется достаточная версия PHP
- Файлы `.phar` могут быть выполнены правильно
- Определенные права на каталог достаточны
- Некоторые проблемные расширения не загружен
- Определенные настройки `php.ini` установлены

Когда, ручная установка, не выполняет ни одну из этих проверок, вы должны решить, стоит ли идти на такой компромисс. Ниже описано, как получить Composer вручную:

    curl -s http://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Путь `$HOME/local/bin` (или папка выбранная вами) должна находиться в вашей переменной окружения `$PATH`. Это позволит быть доступной команде `composer`.

Если вы прочтете документацию Composer, которая гласит, что нужно запускать Composer так `php composer.phar install`, вы можете заменить эту команду так:

    composer install

### Как объявить и установить зависимости

Во-первых, создайте файл `composer.json` в той-же директории, что и `composer.phar`. Вот пример списка для [Twig][2], в качестве зависимости проекта.

	{
	    "require": {
	        "twig/twig": "1.8.*"
	    }
	}

Далее, запустить эту команду из вашей корневой директории проекта.

    php composer.phar install

Это позволить загрузить и установить зависимости проекта в папку `vendors/`. Далее, добавьте эту линию в основной PHP файл вашего приложения; это укажет PHP использовать автозагрузчик Composer для зависимостей вашего проекта.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Теперь вы можете использовать зависимости вашего проетка и они будут автоматически загружаться по требованию.

* [Подробнее о Composer][3]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: http://getcomposer.org/doc/00-intro.md
