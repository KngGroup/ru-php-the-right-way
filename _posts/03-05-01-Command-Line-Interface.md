---
title: Интерфейс командной строки
isChild: true
---

## Интерфейс командной строки

Главная цель с которой был создан PHP, писать веб приложения, но он так-же полезен для написания кода для интерфейса командной строки(CLI). PHP программы командной строки, могут помочь вам автоматизировать общие задачи, как тестирование, развертывание и администратирование приложения.

CLI PHP программы очень мощные, потому что вы можете использовать код вашего приложения напрямую, буз нужды в создании и обеспечении безопасности веб-интерфейса(GUI) для него. Только убедитесь, что вы используете для ваших скриптов CLI PHP публичный корень вашего веб-сервера. 

Попробуйте запустить PHP из консоли:

{% highlight bash %}
> php -i
{% endhighlight %}

Опция `-i` выдаст вам конфигурацию вашего PHP, подобно функции [`phpinfo`][phpifno].

Опция `-a` предоставляет доступ к интерактивной оболчки, подобно ruby IRB или интерактивной оболочки python. Так-же есть целый ряд других полезных [опций командной строки][cli-options].

Давайте напишем простую "Привет, $name" программу CLI. Чтобы это сделать, создайте файл с именем `hello.php`, как показано ниже.

{% highlight php %}
<?php
if($argc != 2) {
    echo "Использование: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Привет, $name\n";
{% endhighlight %}

PHP устанавливает две специальные переменные, которые основаны на аргументах, с которыми запущен ваш скрипт. [`$argc`][argc] - это переменная с числовым значением, которая содержит количество аргументов, [`$argv`][argv] - это массив, содержащий значение каждого аргумента. Первый аргумент - всегда название вашего PHP скрипта, в этом случае `hello.php`.

Выражение `exit()` используется с не-нулевым числом, чтобы дать оболочке понять, что команда не удалась.
Часто используемые коды завершения можно найти [здесь][exit-codes]

To run our script, above, from the command line:
Чтобы запустить наш скрипт, который указан наверху, из командной строки:

{% highlight bash %}
> php hello.php
Использование: php hello.php [name]
> php hello.php Мир
Привет, Мир
{% endhighlight %}


 * [Подробнее о запуске PHp из командной строки][php-cli]
 * [Подробнее о настройке Windows для запуска PHP из командной строки][php-cli-windows]

[phpinfo]: http://php.net/manual/ru/function.phpinfo.php
[cli-options]: http://www.php.net/manual/ru/features.commandline.options.php
[argc]: http://php.net/manual/ru/reserved.variables.argc.php
[argv]: http://php.net/manual/ru/reserved.variables.argv.php
[php-cli]: http://php.net/manual/ru/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/ru/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits