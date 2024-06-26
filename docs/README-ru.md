# Xiaomi HyperOS Обход загрузчика

![Версия: 1.0](https://img.shields.io/badge/Version-1.0-brightgreen?style=for-the-badge) [![中文文档](https://img.shields.io/badge/中文文档-brightgreen?style=for-the-badge)](README-zh.md) [![日本語](https://img.shields.io/badge/日本語-brightgreen?style=for-the-badge)](README-ja.md)

PoC, использующий уязвимость для обхода ограничений сообщества Xiaomi HyperOS на разблокировку загрузчика.

## 💘 php-adb

Проект с гордостью использует [php-adb](https://github.com/MlgmXyysd/php-adb) библиотеку.

## ⚠️ Предупреждение

После разблокировки загрузчика, вы можете столкнуться со следующими проблемами:

- Программное или аппаратное обеспечение не работает должным образом или даже повреждено.
- Потеря данных, хранящихся на устройстве.
- Кража кредитной карты или другие финансовые потери.

Если вы столкнулись с чем-либо из вышеперечисленного, вам следует взять всю ответственность на себя, поскольку это риск, с которым вы можете столкнуться при разблокировке загрузчика. Очевидно, что это не покрывает всех рисков. Вы были предупреждены.

- Потеря гарантии. Не только базовая гарантия, но и некоторые дополнительные расширенные гарантии (например, Mi Care или гарантия на разбитый экран), которые вы приобрели, также могут быть утрачены в соответствии с исключениями, предусмотренными Xiaomi.
- Самоуничтожение на аппаратном уровне, как в Samsung Knox. Функции, связанные с TEE, будут безвозвратно повреждены. Восстановить их можно только путем замены материнской платы.
- Функциональные аномалии после прошивки сторонней системы из-за закрытого исходного кода ядра.
- Телефон или аккаунт заблокирован при разблокировке загрузчика.

If you're experiencing any of the above, consider yourself damned. Ever since Xiaomi restricted unlocking BootLoader, it has been against Xiaomi's 'geek' spirit and even the GPL. Xiaomi's restrictions on BootLoader unlocking are endless, and there's nothing we as developers can do about it.

## 📲 Требования к разблокировке

- Действующее устройство:
  - Разблокированное\* Xiaomi, Redmi или POCO устройство.
  - На вашем устройстве запущена официальная версиюя HyperOS. 
  - (Обновление 2023/11/23) Ваше устройство не принудительно проверяет квалификацию учетной записи Xiaomi.
- Действующая SIM-карта:
  - \* За исключением планшетов, которые не могут использовать SIM-карты.
  - SIM-карта не должна быть нерабочей.
  - SIM-карта должна иметь доступ в Интернет.
  - В течение трех месяцев разрешается разблокировать только 2 устройства на одну действующую SIM-карту.
- Действующая учетная запись Xiaomi:
  - незаблокированный\* аккаунт Xiaomi.
  - Каждый аккаунт может разблокировать только 1 телефон в месяц и 3 телефона в год.
- Вы прочитали и поняли [Предупреждение](#%EF%B8%8F-warning) привиденное выше.

- \*  Согласно инструкции по разблокировке, предоставленной Xiaomi, она запретит некоторым аккаунтам и устройствам использовать инструмент разблокировки, что называется "контролем риска".

## ⚙️ Как использовать?

1. Загрузите и установите PHP 8.0+ для вашей операционной системы с [официального сайта](https://www.php.net/downloads).
2. Включите расширение OpenSSL и Curl в файле `php.ini`. (И/или установите `extension_dir` в каталог PHP `ext` директорию, если скрипт не сработал.)
3. Разместите файл `adb.php` в [php-adb](https://github.com/MlgmXyysd/php-adb) в директорию.
4. Загрузите [platform-tools](https://developer.android.com/studio/releases/platform-tools) и поместите их в `libraries`. *Примечание: в Mac OS необходимо переименовать `adb` в `adb-darwin`.
5. Откройте терминал и с помощью интерпретатора PHP выполните [скрипт](../bypass.php).

- p.s. В релизы упакованы необходимые файлы и скрипты, запускаемые по щелчку мыши.

6. Нажмите несколько раз на `Настройки - О телефоне- MIUI версия` чтобы включить `Режим разработчика`.
7. Включите `OEM-разблокировку`, `Отладка по USB` and `Отладка по USB (настройки безопасности)` in `Settings - Additional Settings - Development Options`.
8. Войдите в _действительную_\* учетную запись Xiaomi.
9. Подключите телефон к компьютеру через проводной интерфейс 
10. Установите флажок `Всегда разрешать с этого компьютера` и нажмите `OK`.

- \* См. раздел "[Требования к разблокировке](#-Unlocking-requirements)" или выше.

11. Подождите и следуйте подсказкам сценария.
12. После успешной привязки вы можете использовать [официальный инструмент разблокировки](https://en.miui.com/unlock/index.html), чтобы проверить время, которое вам нужно подождать.
13. Во время ожидания пользуйтесь устройством в обычном режиме, не вынимайте SIM-карту, не выходите из учетной записи и не выключайте функцию `Найти мой телефон`, а также не привязывайте устройство повторно до тех пор, пока оно не будет успешно разблокировано. Устройство будет автоматически отправлять пакеты `HeartBeat` на сервер время от времени.

## 📖 Обходной путь
- Проводится техническое обслуживание...

## 🔖 Вопросы и ответы

 - Вопрос: Почему инструмент разблокировки все еще напоминает мне о необходимости подождать 168/360 (или более) часов?
  - Ответ: В принципе, этот PoC позволяет обойти ограничения, добавленные для HyperOS. Вам по-прежнему необходимо соблюдать ограничения для MIUI.

- Вопрос: Устройство выдает сообщение `Не удалось проверить, подождите минуту или две и повторите попытку`.
  - Ответ: Это нормально, запрос на привязку на стороне устройства был заблокирован нашим скриптом. Фактический результат привязки зависит от запроса скрипта.

- Вопрос: Привязка не удалась с кодом ошибки `401`.
  - Ответ: Срок действия учетных данных вашей учетной записи Xiaomi истек, вам необходимо выйти и снова войти в систему на вашем устройстве.

- Вопрос: Привязка не удалась с кодом ошибки `20086`.
  - Ответ: Срок действия учетных данных вашего устройства истек, вам необходимо перезагрузить устройство.

- Вопрос: Привязка не удалась с кодом ошибки `20090` или `20091`.
  - Ответ: Сбой функции диспетчера учетных данных устройства безопасности, обратитесь в отдел продаж.

- Вопрос: Привязка не удалась с кодом ошибки `30001`.
  - Ответ: Ваше устройство было принудительно проверено Xiaomi для подтверждения квалификации учетной записи. Xiaomi давно потеряла свой "гиковский" дух, и мы ничего не можем с этим поделать.

## ⚖️ Лицензия

Без лицензии, вам разрешено использовать только этот проект. Все авторские права (и ссылки, и т.д.) на это программное обеспечение не могут быть удалены или изменены без разрешения. Все права защищены [MeowCat Studio](https://github.com/MeowCat-Studio), [Meow Mobile](https://github.com/Meow-Mobile) и [NekoYuzu](https://github.com/MlgmXyysd).
