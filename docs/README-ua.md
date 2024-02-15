# Xiaomi HyperOS BootLoader Bypass

![Версія: 1.0](https://img.shields.io/badge/Version-1.0-brightgreen?style=for-the-badge) [![中文文档](https://img.shields.io/badge/中文文档-brightgreen?style=for-the-badge)](README-zh.md) [![日本語](https://img.shields.io/badge/日本語-brightgreen?style=for-the-badge)](README-ja.md)

PoC, що використовує уразливість для обходу обмежень спільноти Xiaomi HyperOS на прив'язку розблокованих облікових записів BootLoader.

Не соромтеся створювати пул реквест :)

## 💘 php-adb

Проект з гордістю використовує бібліотеку [php-adb](https://github.com/MlgmXyysd/php-adb).

## ⚠️ Попередження

Після розблокування завантажувача, ви можете зіткнутися з наступними проблемами:

- Програмне або апаратне забезпечення працює з помилками або навіть пошкоджене.
- Втрата даних, збережених на пристрої.
- Врадений номер кредитної карти або інші фінансові втрати.

Якщо ви зіткнулись з вище перерахованими проблемами, знайте ви берете відповідальність на себе, оскільки це риск з яким ви можете зіткнутися при розблокуванні завантажувача. Очевидно, що це не покриває всі риски. Але ви були попереджені 

- Втрата гарантії. Не тільки базова гарантія, а й деякі додаткові розширені гарантії (наприклад, Mi Care або гарантія на розбитий екран), які ви придбали, також можуть бути втрачені відповідно до винятків, передбачених Xiaomi.
- Самознищення на апаратному рівні, як у Samsung Knox. Функції, пов'язані з TEE, будуть безповоротно пошкоджені. Відновити їх можна тільки шляхом заміни материнської плати.
- Функціональні аномалії після прошивки сторонньої системи через закритий вихідний код ядра.
- Телефон або акаунт заблоковано під час розблокування завантажувача.

Якщо ви зіткнулись з чимось перерахованим вище, вважайте, що в вас не найкращий день. Відколи Xiaomi обмежила розблокування BootLoader, це суперечить "гіківському" духу Xiaomi і навіть GPL. Обмеження Xiaomi на розблокування BootLoader нескінченні, і ми, як розробники, нічого не можемо з цим вдіяти.

## 📲 Вимоги до розблокування

- Чинний пристрій:
  - Розблокований пристрій\* Xiaomi, Redmi або POCO.
  - На вашому пристрої працює офіційна версія HyperOS. 
  - (Оновлено 2023/11/23) Ваш пристрій не перевіряє примусово кваліфікацію облікового запису Xiaomi.
- Чинна SIM-карта:
  - \* За виключенням планшетів, які не можуть використовувати SIM-карти.
  - SIM-карта має бути робочою.
  - SIM-карта має мати доступ до інтернету.
  - Протягом трьох місяців можна розблокувати тільки 2 телефони з допомогою однієї сім карти.
- Чинний обліковий запис Xiaomi:
  - Не заблокований\* аккаунт Xiaomi.
  - Кожен аккаунт може розблокувати лише 1 телефон в месяц і 3 телефони в рік.
- Ви прочитали и прийняли [Попередження](#%EF%B8%8F-warning) описане вище.

- \*  Згідно з інструкцією з розблокування, наданою Xiaomi, вона заборонить деяким акаунтам і пристроям використовувати інструмент розблокування, який називається "контроль ризиків".

## ⚙️ Спосіб використання?

1. Завантажте й встановіть PHP 8.0+ для вашої операційної системи з [офіційного вебсайту](https://www.php.net/downloads).
2. Ввімкніть розширення OpenSSL та Curl в файлі `php.ini`. (Або встановіть `extension_dir` в каталог PHP `ext` діректорію, якщо скрипт не спрацював.)
3. Размістіть файл `adb.php` в [php-adb](https://github.com/MlgmXyysd/php-adb) в директорії.
4. Завантажте [platform-tools](https://developer.android.com/studio/releases/platform-tools) і перемістіть їх в `libraries`. *Нотатка: для Mac OS необхідно перейменувати `adb` в `adb-darwin`.
5. Відкрийте термінал і з допомогою інтерпритатора PHP виконайте [скрипт](../bypass.php).

- p.s. Необхідні файли та скрипти для запуску за кліком є в релізах.

6. Натисніть кілька разів на `Налаштування - Про телефон - Версія MIUI`, щоб увімкнути `Режим розробника`.
7. Ввімкніть `OEM Розблокування`, `Налагодження USB` and `Налагодження USB (Налаштування безпеки)` in `Налаштування - Розширені налаштування - Режим розробника`.
8. Ввійдіть в _дійсний_\* акаунт Xiaomi.
9. Під'єднайте телефон до ПК за допомогою кабелю.
10. Виберіть `Завжди дозволяти з цього комп'ютеру ` та клікніть `Oкей`.

- \* See "[Unlocking Requirements](#-Unlocking-requirements)" above.

11. Wait and follow the prompts of script.
12. After successful binding, you can use the [official unlock tool](https://en.miui.com/unlock/index.html) to check the time you need to wait.
13. During the waiting period, please use the device normally, keep the SIM card inserted, do not log out of your account or turn off `Find My Phone`, and do not re-bind the device until it is successfully unlocked. The device will automatically send `HeartBeat` packets to the server every once in a while.

## 📖 Workaround

- Undergoing maintenance...

## 🔖 FAQs

- Q: Why does the unlock tool still remind me to wait 168/360 (or more) hours?
  - A: By principle, this PoC only bypasses the restrictions added for HyperOS. You still need to comply with the restrictions for MIUI.

- Q: The device shows `Couldn't verify, wait a minute or two and try again`.
  - A: This is normal, the binding request on the device side has been blocked by our script. The actual binding result is subject to the script prompt.

- Q: Binding failed with error code `401`.
  - A: Your Xiaomi account credentials have expired, you need to log out and log in again in your device.

- Q: Binding failed with error code `20086`.
  - A: Your device credentials have expired, you need to reboot your device.

- Q: Binding failed with error code `20090` or `20091`.
  - A: Device's Security Device Credential Manager function failure, contact after-sales.

- Q: Binding failed with error code `30001`.
  - A: Your device has been forced to verify the account qualification by Xiaomi. Xiaomi lost its 'geek' spirit a long time ago, and there's nothing we can do about it.

- Q: Binding failed with error code `86015`.
  - A: The server has rejected this bind request, please try again.

## ⚖️ License

No license, you are only allowed to use this project. All copyright (and link, etc.) in this software is not allowed to be deleted or changed without permission. All rights are reserved by [MeowCat Studio](https://github.com/MeowCat-Studio), [Meow Mobile](https://github.com/Meow-Mobile) and [NekoYuzu](https://github.com/MlgmXyysd).
