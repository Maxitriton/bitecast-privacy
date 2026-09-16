# Політика приватності BiteCast

**Чинна з:** _(дата першої публікації в Google Play)_

## Коротко

BiteCast не має акаунтів, не збирає статистики, не показує реклами й нікому не продає даних. Усе, що ви створюєте в додатку — збережені водойми, ваші точки на місцевості, проміри глибин, записи щоденника, фото, налаштування — лишається на вашому телефоні.

Само собою з телефона виходить одне: координати точки, для якої потрібен прогноз погоди, і запити тайлів карти. Є ще один шлях, і він відкривається тільки вашим натисканням: кнопка «Навігація» передає координати точки тому картографічному додатку, який ви оберете.

## Що ніколи не залишає телефон

- **Записи щоденника:** дати, години, вид риби, кількість, оцінка клювання, нотатки.
- **Фото уловів.** У базі зберігається лише шлях до файла, а не сам знімок; файл лишається там, куди його поклала камера чи галерея.
- **Збережені водойми** та назви, які ви їм дали.
- **Ваші точки** — координати, назви й похибка GPS у момент зняття.
- **Проміри глибин** — і поставлені вручну, і завантажені з ехолота (CSV, GPX, `.sl2`, `.sl3`). Файл треку читається на пристрої.
- **Накопичена історія погоди** для ваших водойм.
- **Налаштування:** мова, тема, вид риби, тип водойми, вмикання навчання й сповіщень.

Ці дані зберігаються всередині пісочниці додатка на вашому пристрої.

## Що виходить назовні — і кому

**1. Координати → MET Norway** (`api.met.no`), щоб отримати прогноз погоди. Надсилається лише широта й довгота, округлені до чотирьох знаків після коми (приблизно 110 метрів), і рядок з назвою додатка, якого вимагають умови сервісу. Жодного ідентифікатора телефона, акаунта чи вашого імені там немає. Обробка даних на боці MET Norway регулюється їхніми умовами.

**2. Запити тайлів карти → OpenFreeMap** (`tiles.openfreemap.org`), щоб намалювати карту. Як і будь-який запит в інтернет, він показує серверу вашу IP-адресу й те, яку ділянку карти ви дивитесь. Додаток не додає до цих запитів нічого свого.

**3. Пошук місця й визначення країни → геокодер операційної системи.** Коли ви шукаєте населений пункт, якого немає у вбудованому довіднику, або коли додаток визначає країну для нерестових заборон, запит виконує сама операційна система. Куди вона його спрямує і що там зберігає — регулюється політикою приватності виробника пристрою та служб Google.

**4. Резервна копія у файл, який робите ви самі.** Додаток збирає ваші водойми, точки, проміри, щоденник і налаштування в один файл і кладе його туди, куди ви вкажете. Цей файл нікуди не надсилається. Фото уловів у нього не входять — у базі зберігається лише шлях до знімка.

**5. Автоматична копія Android → ваш Google Drive.** Це робить операційна система, а не додаток. Якщо резервне копіювання ввімкнене у вашому телефоні, Android час від часу копіює дані BiteCast у ваш власний Google Drive і повертає їх при перевстановленні або переході на новий телефон. Ця копія належить вашому акаунту й підпадає під правила Google; ми до неї доступу не маємо. Вимкнути це можна в налаштуваннях телефона: «Налаштування Google → Резервне копіювання».

**6. Координати точки → картографічний додаток, який ви оберете.** Це відбувається лише коли ви натискаєте «Навігація». Операційна система показує список додатків, які вміють карти, і туди йде координата точки з її назвою. Далі ці дані живуть за правилами того додатка. Якщо жоден додаток не візьме точку, вона відкриється на карті OpenStreetMap у браузері — тоді координата видна серверу `openstreetmap.org`.

Це весь перелік. Інших мережевих звернень у додатку немає.

## Дозволи

Додаток просить дванадцять дозволів.

**Використовуються безпосередньо:**

- `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION` — щоб знати, для якої води рахувати прогноз, визначити країну для нерестових заборон і зняти точку там, де ви стоїте;
- `INTERNET`, `ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE` — прогноз погоди й тайли карти;
- `POST_NOTIFICATIONS` — нагадування напередодні доброго дня, і лише якщо ви його ввімкнули.

**Потрібні для роботи функцій, які ви запускаєте самі:**

- `READ_EXTERNAL_STORAGE`, `WRITE_EXTERNAL_STORAGE` — вибір фото улову й запис файла резервної копії. Лише на Android 12 і старіших версіях;
- `RECEIVE_BOOT_COMPLETED`, `WAKE_LOCK`, `VIBRATE` — щоб заплановане нагадування пережило перезавантаження телефона й пролунало;
- `com.bitecast.app.DYNAMIC_RECEIVER_NOT_EXPORTED_PERMISSION` — службовий дозвіл Android, яким системна бібліотека захищає власні внутрішні повідомлення від інших застосунків.

**Місцезнаходження** використовується лише коли додаток відкритий. У фоні воно не збирається. Постійне визначення положення вмикається у трьох випадках і лише поки відкритий відповідний екран: під час зняття точки, у картці точки з відстанню до неї та в компасі. Щойно екран закрито, воно вимикається.

**Доступ до фото** запитується лише в момент, коли ви самі додаєте знімок до запису.

**Сповіщення локальні:** текст готується на самому телефоні.

Відмова від будь-якого дозволу не ламає додаток: без місцезнаходження можна вибрати водойму вручну, без фото — вести щоденник без знімків, без сповіщень — дивитися прогноз самому.

## Бібліотеки у складі додатка

У складі додатка є бібліотека **Firebase Cloud Messaging** — вона входить до модуля сповіщень і окремо з нього не вилучається. Додаток нею не користується: він показує лише власні сповіщення, заплановані на телефоні, і ніде не запитує push-токена. У збірці немає файла конфігурації Firebase, тому бібліотека не реєструється й нічого не надсилає.

## Зберігання й видалення

Дані зберігаються, доки ви їх не видалите. Видалення додатка стирає все: базу, налаштування й накопичену історію погоди. Окремі записи щоденника, проміри, точки та збережені водойми видаляються в самому додатку; при видаленні запису прибирається й доданий до нього файл знімка.

Оновлення додатка нічого не стирає.

Резервних копій на наших серверах не існує, бо серверів немає. Якщо ввімкнене автоматичне копіювання Android, дані можуть повернутися з вашого Google Drive після перевстановлення.

## Діти

Додаток не призначений для дітей і не збирає даних свідомо від них.

## Чого в додатку немає

Немає акаунтів і входу, немає реклами, немає аналітики й лічильників, немає жодного стороннього набору для стеження. Ми не продаємо й не передаємо дані третім особам, бо не маємо їх у себе.

## Зміни в цій політиці

Істотні зміни супроводжуються оновленням дати чинності вгорі цієї сторінки та примітками в описі додатка в Google Play.

## Зв'язок

Питання щодо приватності: **bitecast.original@gmail.com**

---

# Privacy Policy — BiteCast

**Effective:** _(date of first Google Play release)_

## In short

BiteCast has no accounts, collects no analytics, shows no ads and sells no data to anyone. Everything you create in the app — saved waters, your own marks, depth soundings, journal entries, photos and settings — stays on your phone.

Only one thing leaves the phone on its own: the coordinates of the spot you want a forecast for, and map tile requests. One more path exists and it opens only when you tap it: the "Navigate" button hands the coordinates of your mark to whichever maps app you choose.

## What never leaves the phone

- **Journal entries:** dates, hours, species, counts, bite rating, notes.
- **Catch photos.** The database stores only the file path, not the image itself.
- **Saved waters** and the names you gave them.
- **Your marks** — coordinates, names and the GPS accuracy at the moment of capture.
- **Depth soundings** — both placed by hand and imported from a fish finder (CSV, GPX, `.sl2`, `.sl3`). The track file is read on the device.
- **Accumulated weather history** for your waters.
- **Settings:** language, theme, target species, water type, learning and notification switches.

This data is stored inside the app's sandbox on your device.

## What does leave, and to whom

**1. Coordinates → MET Norway** (`api.met.no`), to obtain the weather forecast. Only latitude and longitude rounded to four decimal places (about 110 metres) are sent, along with the app identification string their terms require. No device identifier, account or name is included. Processing on MET Norway's side is governed by their terms.

**2. Map tile requests → OpenFreeMap** (`tiles.openfreemap.org`), to draw the map. Like any internet request, it reveals your IP address and which part of the map you are viewing. The app adds nothing of its own to these requests.

**3. Place search and country detection → the operating system's geocoder.** When you search for a settlement that is not in the built-in directory, or when the app determines the country for closed-season rules, the request is performed by the operating system itself. Where it is routed and what is stored there is governed by the privacy policy of your device manufacturer and of Google services.

**4. A backup file that you create yourself.** The app collects your waters, marks, soundings, journal and settings into a single file and puts it where you choose. This file is not sent anywhere. Catch photos are not included — the database stores only the path to the image.

**5. Android automatic backup → your own Google Drive.** This is done by the operating system, not by the app. If backup is enabled on your phone, Android periodically copies BiteCast data to your own Google Drive and restores it on reinstall or on a new phone. That copy belongs to your account and is governed by Google's rules; we have no access to it. You can turn it off in your phone settings: "Google Settings → Backup".

**6. Coordinates of a mark → the maps app you choose.** This happens only when you tap "Navigate". The operating system shows the list of apps that handle maps, and the coordinate with its name goes there. From that point the data lives by that app's rules. If no app takes the mark, it opens on the OpenStreetMap website — then the coordinate is visible to `openstreetmap.org`.

That is the complete list. The app makes no other network requests.

## Permissions

The app requests twelve permissions.

**Used directly:**

- `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION` — to know which water to forecast for, to determine the country for closed-season rules, and to capture a mark where you stand;
- `INTERNET`, `ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE` — weather forecast and map tiles;
- `POST_NOTIFICATIONS` — a reminder the day before a good day, and only if you enabled it.

**Required by features you start yourself:**

- `READ_EXTERNAL_STORAGE`, `WRITE_EXTERNAL_STORAGE` — choosing a catch photo and writing the backup file. On Android 12 and older only;
- `RECEIVE_BOOT_COMPLETED`, `WAKE_LOCK`, `VIBRATE` — so that a scheduled reminder survives a reboot and sounds;
- `com.bitecast.app.DYNAMIC_RECEIVER_NOT_EXPORTED_PERMISSION` — an Android service permission with which a system library protects its own internal broadcasts from other applications.

**Location** is used only while the app is open. It is not collected in the background. Continuous positioning starts in three cases and only while the relevant screen is open: while capturing a mark, in a mark card showing the distance to it, and in the compass. As soon as the screen is closed, it stops.

**Photo access** is requested only at the moment you add an image to an entry yourself.

**Notifications are local:** the text is prepared on the phone itself.

Declining any permission does not break the app: without location you can pick a water manually, without photos you can keep a journal without images, without notifications you can check the forecast yourself.

## Libraries included in the app

The app includes the **Firebase Cloud Messaging** library, which comes as part of the notifications module and cannot be removed from it separately. The app does not use it: it shows only its own notifications scheduled on the phone and never requests a push token. The build contains no Firebase configuration file, so the library does not register and sends nothing.

## Storage and deletion

Data is stored until you delete it. Uninstalling the app erases everything: the database, settings and accumulated weather history. Individual journal entries, soundings, marks and saved waters are deleted inside the app; deleting an entry also removes the image file attached to it.

Updating the app erases nothing.

No backups exist on our servers, because there are no servers. If Android automatic backup is enabled, data may be restored from your Google Drive after reinstalling.

## Children

The app is not intended for children and does not knowingly collect data from them.

## What the app does not have

No accounts and no sign-in, no ads, no analytics or counters, no third-party tracking kit. We do not sell or share data with third parties, because we do not hold it.

## Changes to this policy

Material changes are accompanied by an update to the effective date at the top of this page and by notes in the app's description on Google Play.

## Contact

Privacy questions: **bitecast.original@gmail.com**
