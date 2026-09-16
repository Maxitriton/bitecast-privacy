# Політика приватності BiteCast (Кльов)

**Чинна з:** _(дата першої публікації в Google Play)_

## Коротко

BiteCast **не має акаунтів, не збирає статистики, не показує реклами й нікому
не продає даних**. Усе, що ви створюєте в додатку — збережені водойми, ваші
точки на місцевості, проміри глибин, записи щоденника, фото, налаштування, —
лишається на вашому телефоні.

Само собою з телефона виходить одне: **координати точки, для якої треба
погоду**, — і запити тайлів карти. Є ще один шлях, але він відкривається
**тільки вашим натисканням**: кнопка «Навігація» передає координати точки
тому картографічному додатку, який ви оберете. Нижче докладно, кому саме
й навіщо.

## Що ніколи не залишає телефон

- **Записи щоденника**: дати, години, вид риби, кількість, оцінка клювання, нотатки.
- **Фото уловів.** У базі зберігається лише **шлях до файла**, а не сам знімок; файл
  лишається там, куди його поклала камера чи галерея. Нікуди не надсилається.
- **Збережені водойми** та їхні назви, які ви вписали.
- **Ваші точки** — координати, назви, які ви їм дали, і похибка GPS у момент
  зняття. Це найточніше, що є в базі: коряга, грибне місце чи вишка з точністю
  до метрів. Нікуди не надсилається й ніде не дублюється, доки ви самі
  не натиснете «Навігація» (див. пункт 6 нижче).
- **Проміри глибин** — і поставлені вручну, і завантажені з ехолота (CSV, GPX,
  `.sl2`/`.sl3`). Файл треку читається на пристрої й не передається далі.
- **Накопичена історія погоди** для ваших водойм.
- **Налаштування**: мова, тема, вид риби, тип водойми, вмикання навчання й сповіщень.

Ці дані живуть у базі SQLite й локальному сховищі всередині пісочниці додатка.

## Що виходить назовні — і кому

**1. Координати → MET Norway** (`api.met.no`), щоб отримати прогноз погоди. Надсилається
**тільки широта й довгота, округлені до чотирьох знаків** (це приблизно 110 метрів),
і рядок з назвою додатка, якого вимагають умови MET. Жодного ідентифікатора телефона,
акаунта чи вашого імені там немає, і жодні інші дані додатка туди не йдуть. Обробка
даних на боці MET — за їхніми умовами (CC BY 4.0, met.no).

**2. Запити тайлів карти → OpenFreeMap** (`tiles.openfreemap.org`), щоб намалювати карту.
Як і будь-який запит в інтернет, він показує серверу вашу IP-адресу й те, яку ділянку
карти ви дивитесь. Ми не додаємо до цих запитів нічого свого.

**3. Пошук місця й визначення країни → геокодер операційної системи.** Коли ви шукаєте
населений пункт, якого немає в нашому вбудованому довіднику, або коли додаток визначає
країну для нерестової заборони й геоблоку, запит виконує **сама Android**, а не ми. Куди
його спрямує система (як правило, до сервісів Google) і що вона там зберігає — поза нашим
контролем і регулюється політикою приватності виробника пристрою та служб Google.

**4. Резервна копія — у файл, який робите ви самі.** На вкладці «Ще» є кнопка
«Зберегти у файл»: додаток збирає ваші водойми, точки, проміри, щоденник
і налаштування в один файл JSON і кладе його **туди, куди вкажете ви** — у теку
на телефоні, на картку пам'яті або в теку хмарного диска, якщо оберете саме її.
Ми цього файла нікуди не надсилаємо й не бачимо. Фото уловів у файл не входять:
у базі зберігається лише шлях до знімка.

**5. Автоматична копія Android → ваш Google Drive.** Це робить **сама
операційна система**, а не ми: Android має вбудоване резервне копіювання
додатків і, якщо воно ввімкнене у вашому телефоні, час від часу копіює дані
BiteCast — базу з водоймами, точками, промірами й щоденником — у ваш власний
Google Drive. При перевстановленні додатка або переході на новий телефон
Android повертає їх звідти сам.

Ми лишили це ввімкненим свідомо: інакше людина, яка не зробила копію руками,
втрачала б усе разом зі старим телефоном. Але сказати про це треба прямо:
**копія лежить у Google Drive, і поки вона там, вона підпадає під правила
Google, а не наші.** Дані належать вашому акаунту, не нам — ми до цієї копії
доступу не маємо й не бачимо її.

Вимкнути це можна не в нашому додатку, а в телефоні: «Налаштування Google →
Резервне копіювання». Якщо вимкнете — лишається копія у файл, яку ви робите
самі (пункт 4 вище).

**6. Координати точки → картографічний додаток, який ви оберете.** Це
відбувається **лише коли ви натискаєте «Навігація»** в картці своєї точки, і
жодного разу без цього. Android показує список додатків, які вміють карти
(Google Maps, Organic Maps, OsmAnd та інші), і туди йде **координата точки
з її назвою**. Далі ці дані живуть за правилами того додатка, а не за нашими,
і ми на них уже не впливаємо. Якщо жоден додаток не візьме точку, вона
відкриється на карті OpenStreetMap у браузері — тоді координата видна
серверу openstreetmap.org.

Це весь перелік. Інших мережевих звернень у додатку немає.

## Дозволи й навіщо вони

- **Місцезнаходження** — щоб знати, для якої води рахувати прогноз, щоб
  визначити країну для нерестових заборон і щоб зняти вашу точку там, де ви
  стоїте. Використовується лише коли додаток відкритий; у фоні
  місцезнаходження не збирається. Постійне стеження за положенням вмикається
  рівно у трьох випадках і лише поки ви дивитесь на відповідний екран: поки
  триває зняття точки (до 30 секунд, щоб дочекатися доброї точності), поки
  відкрита картка точки з відстанню до неї, і поки відкритий компас — там
  положення потрібне, щоб порахувати напрямок на точку. Щойно екран закрито,
  стеження гасне саме.
- **Магнітний датчик (компас)** — окремого дозволу Android для нього не питає.
  Він міряє магнітне поле в самому телефоні, нікуди нічого не надсилає й
  працює без мережі та без GPS.
- **Доступ до фото** — тільки в момент, коли ви самі додаєте знімок до запису.
- **Сповіщення** — щоб надіслати нагадування про хороший день. Сповіщення
  **локальні**: текст готується на самому телефоні, ніякий сервер його не бачить
  і не надсилає.

Відмова від будь-якого з дозволів не ламає додаток: без місцезнаходження можна
вибрати водойму вручну, без фото — вести щоденник без знімків, без сповіщень —
дивитися прогноз самому.

## Зберігання й видалення

Дані зберігаються, доки ви їх не видалите. **Видалення додатка стирає все:**
базу, налаштування й накопичену історію погоди. Окремі записи щоденника,
проміри, точки на воді та збережені водойми видаляються в самому додатку;
при видаленні запису прибирається й доданий до нього файл знімка.

Резервних копій на наших серверах не існує, бо серверів немає.

**Оновлення додатка нічого не стирає** — усе лишається на місці. Дані зникають
при видаленні додатка або при очищенні його даних у налаштуваннях телефона —
але й тоді Android може повернути їх зі своєї копії (пункт 5 вище), якщо вона
ввімкнена. Незалежно від неї є **резервна копія у файл** (пункт 4): зробіть її
самі, і при заміні телефона все повернеться навіть без Google.

## Діти

Додаток не призначений для дітей і не збирає даних свідомо від них.

## Чого в додатку немає

Немає акаунтів і входу, немає реклами, немає аналітики й лічильників, немає
жодного стороннього набору для стеження. Ми не продаємо й не передаємо дані
третім особам, бо не маємо їх у себе.

**Одне уточнення, яке чесніше сказати самим.** У складі додатка є бібліотека
**Firebase Cloud Messaging** — вона приїжджає разом із модулем сповіщень
(`expo-notifications`) і окремо її звідти не витягнути. Ми нею **не
користуємося**: додаток показує лише **власні сповіщення, заплановані на
телефоні** (нагадування напередодні доброго дня), і ніде не запитує
push-токена. Головне: у збірці **немає файла конфігурації Firebase**
(`google-services.json`), тобто бібліотеці нема до якого проєкту під'єднатися —
вона не реєструється й нічого нікуди не надсилає. Перевірити це можна ззовні:
у ресурсах готового APK немає ані `google_app_id`, ані `gcm_defaultSenderId`.
Якщо колись з'явиться справжній push, цей абзац зміниться **до** того, як він
запрацює.

## Що зміниться в майбутньому — і чого ще немає

Плануються дві речі, яких **зараз у додатку немає**:

- **Обмін промірами глибин між рибалками.** Якщо він з'явиться, ділитися можна
  буде лише за явною згодою й окремо для кожної водойми; передаватимуться
  **тільки координата й глибина**, ніколи назви ваших місць, нотатки чи улови.
- **Підписка й вхід через Google.**

Обидві змінять цей документ **до** того, як запрацюють, а не після.

## Зміни в цій політиці

Істотні зміни супроводжуються оновленням дати вгорі та примітками в описі
додатка в Google Play.

## Дозволи, які просить додаток

Знято з готової збірки **0.39.0** — **дванадцять** записів у маніфесті. Перелік
потрібен для форми Data safety у Google Play, і тут він розібраний чесно.

✅ **Було тридцять, стало дванадцять — 14 вересня 2026.** Правовий аудит на запит
замовника показав, що вісімнадцять дозволів додаток **не використовує взагалі**:
їх приносила бібліотека нагадувань. Доти в цьому документі стояло, що прибрати
їх «можна лише відмовою від бібліотеки». ⚠️ **Це було неправдою**, і перевірили
ми її лише коли дійшли руки виміряти: у коді **нуль** звернень до push і **нуль**
до значків на іконці, а `google-services.json` (без якого Firebase не вмикається)
у проєкті немає взагалі. Тож усі вісімнадцять просто вилучені з маніфесту через
`blockedPermissions` у `app.json`, а локальні нагадування працюють як працювали.

**Ті, що додаток справді використовує (шість):**

- `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION` — де ви стоїте: без цього немає
  ні прогнозу для поточного місця, ні збереження точки;
- `INTERNET`, `ACCESS_NETWORK_STATE`, `ACCESS_WIFI_STATE` — погода й тайли карти;
- `POST_NOTIFICATIONS` — нагадування про добрий день, і лише якщо ви його ввімкнули.

**Ті, що прийшли з бібліотеками й лишилися, бо потрібні (шість):**

- `READ_EXTERNAL_STORAGE`, `WRITE_EXTERNAL_STORAGE` — вибір фото улову й запис файлу
  резервної копії (лише на Android 12 і старіших: `maxSdkVersion="32"`);
- `RECEIVE_BOOT_COMPLETED`, `WAKE_LOCK`, `VIBRATE` — щоб заплановане нагадування
  пережило перезавантаження телефона й пролунало;
- `com.bitecast.app.DYNAMIC_RECEIVER_NOT_EXPORTED_PERMISSION` — службовий дозвіл
  самого Android, яким системна бібліотека захищає власні внутрішні повідомлення
  від інших застосунків. Назовні він не веде нікуди.

**Чого більше немає (вісімнадцять):** `com.google.android.c2dm.permission.RECEIVE`
(Firebase Cloud Messaging — **push ми не надсилали й сервера не маємо**),
`BIND_GET_INSTALL_REFERRER_SERVICE` (службовий дозвіл Google Play),
`READ_APP_BADGE` і п'ятнадцять дозволів на **значок з числом на іконці** для
лаунчерів Samsung, Huawei, Sony, HTC, Oppo та інших — серед них були й такі,
що дозволяли **читати налаштування лаунчера**. Додаток числа на іконці не малював
ніколи.

## Зв'язок

Питання щодо приватності: **bitecast.original@gmail.com**

---

# Privacy Policy — BiteCast

**Effective:** _(date of first Google Play release)_
**App version:** 0.27.0 (permission list taken from build 0.25.1)

## In short

BiteCast has **no accounts, no analytics, no advertising, and sells no data**.
Everything you create — saved waters, your own saved points, depth soundings,
catch log entries, photos, settings — stays on your phone.

On its own the device sends one thing: **the coordinates of the point you want
weather for**, plus map tile requests. One further path exists but opens **only
when you press it**: the «Navigate» button hands a point's coordinates to the map
app you choose. Details below.

## What never leaves your phone

- **Catch log entries**: dates, hours, species, counts, bite rating, notes.
- **Catch photos.** Only a **file path** is stored, never the image itself; the file
  stays where your camera or gallery put it. It is never uploaded.
- **Saved waters** and the names you gave them.
- **Your own points** — coordinates, the names you gave them, and the GPS accuracy
  at the moment they were taken. These are the most precise data in the app: a
  snag, a mushroom patch or a deer stand down to metres. Nothing is sent anywhere
  until you press «Navigate» yourself (item 6 below).
- **Depth soundings** — both tapped by hand and imported from an echo sounder (CSV, GPX,
  `.sl2`/`.sl3`). Track files are parsed on the device only.
- **Accumulated weather history** for your waters.
- **Settings**: language, theme, target species, water type, learning and notification
  switches.

## What does leave, and to whom

**1. Coordinates → MET Norway** (`api.met.no`) to fetch the forecast. Only
**latitude and longitude rounded to four decimals** (about 110 metres) are sent,
together with the application identifier string MET's terms require. No device
identifier, no account, no other app data. MET's own terms govern their side.

**2. Map tile requests → OpenFreeMap** (`tiles.openfreemap.org`) to draw the map.
Like any internet request, this reveals your IP address and which part of the map
you are viewing. We add nothing of our own to those requests.

**3. Place search and country detection → the operating system's geocoder.** When
you search for a town that is not in our built-in directory, or when the app
determines the country for spawning bans, **Android performs that lookup**, not
us. Where it routes the request (typically Google services) and what is retained
there is outside our control and governed by your device maker's and Google's
policies.

**4. A backup — into a file you make yourself.** The «More» tab has a «Save to a file»
button: the app collects your waters, points, soundings, catch log and settings
into one JSON file and puts it **where you tell it to** — a folder on the phone,
a memory card, or a cloud drive folder if that is what you pick. We never send
this file anywhere and never see it; if you choose a cloud service folder, from
there it lives by that service's rules. Catch photos are not inside the file:
the database keeps only the path to an image.

**5. Android's automatic backup → your Google Drive.** This is done by **the
operating system**, not by us: Android has built-in app backup and, when it is
enabled on your phone, it periodically copies BiteCast's data — the database
with your waters, points, soundings and catch log — into your own Google Drive.
On reinstall or on a new phone Android restores it from there by itself.

We left this on deliberately: otherwise anyone who never made a backup by hand
would lose everything along with the old phone. But it must be said plainly:
**the copy sits in Google Drive, and while it is there it lives by Google's
rules, not ours.** The data belongs to your account, not to us — we have no
access to that copy and never see it.

You can turn it off in the phone, not in our app: Google settings → Backup.
If you do, the file backup you make yourself (item 4 above) remains.

**6. A point's coordinates → the map app you choose.** This happens **only when
you press «Navigate»** on one of your points, and never otherwise. Android offers
the map apps installed on the phone (Google Maps, Organic Maps, OsmAnd and
others), and the **point's coordinates and name** go to the one you pick. From
there the data lives by that app's rules, not ours. If no app accepts the point,
it opens on the OpenStreetMap website instead, and the coordinates are then
visible to openstreetmap.org.

That is the complete list. The app makes no other network calls.

## Permissions

- **Location** — to know which water to forecast for, to determine the country
  for spawning bans, and to take a point where you are standing. Used only while
  the app is open; never collected in the background. Continuous position updates
  run in exactly three cases and only while you are looking at that screen: while
  a point is being taken (up to 30 seconds, to wait for good accuracy), while a
  point's card is open showing the distance to it, and while the compass is open,
  where a position is needed to work out the bearing to a point. All three stop
  by themselves.
- **Magnetic sensor (compass)** — Android asks no separate permission for it. It
  measures the magnetic field inside the phone, sends nothing anywhere, and works
  without network or GPS.
- **Photos** — only at the moment you attach an image to an entry.
- **Notifications** — for the "good day tomorrow" reminder. Notifications are
  **local**: the text is composed on your phone and no server sees or sends it.

Declining any permission does not break the app.

## Storage and deletion

Data is kept until you delete it. **Uninstalling the app erases everything.**
Individual entries, soundings, points and waters can be deleted in the app;
deleting an entry also removes the photo file attached to it.

There are no backups on our servers, because there are no servers.

**Updating the app erases nothing** — everything stays. Data is lost when the app
is uninstalled or its data is cleared in the phone's settings — though Android may
restore it from its own backup (item 5 above) if that is enabled. Independently of
it there is the **backup file** (item 4): make one yourself and everything comes
back on a new phone, with no Google involved.

## Children

The app is not directed at children and does not knowingly collect their data.

## What is not in the app

No accounts, no advertising, no analytics or trackers, no third-party tracking
SDKs. We do not sell or share data, because we do not hold it.

## Planned, and not present yet

- **Sharing depth soundings between anglers.** If it ships, sharing will require
  explicit consent per water, and only **coordinates and depth** will be sent —
  never your spot names, notes or catches.
- **Subscription and Google sign-in.**

Both will update this document **before** they work, not after.

## Contact

Privacy questions: **bitecast.original@gmail.com**
