# MY TV
Personal launcher for LG webOS / Media Station X.

## Открыть
[Проверить меню в MSX](https://msx.benzac.de/?start=menu:https://dormarig-prog.github.io/my-tv/menu.json).

Если меню уже настроено на телевизоре, полностью закройте и снова откройте MSX либо нажмите «Обновить меню» в разделе «О меню».
Старый URL menu.json сохранён. start.json сохранён и обновлён; копия msx/start.json добавлена для стандартного пути настройки.
При первоначальной настройке MSX использует {SERVER}/msx/start.json. Для хостинга с подпапкой попробуйте сервер dormarig-prog.github.io/my-tv с включённым HTTPS; поддержка ввода пути зависит от версии MSX. Точный стартовый параметр: menu:https://dormarig-prog.github.io/my-tv/menu.json.

## Разделы
- Главная: шесть основных плиток, переход ко всем приложениям, DORMI «Скоро».
- Все приложения: каталог MY TV, добавление через изменение JSON, обновление.
- О меню: управление и ограничения.

## Что запускается
| Плитка | Действие |
|---|---|
| Браузер | link:window:https://ya.ru/ — внешний браузер / отдельное окно, поиск |
| Кинопоиск | Официальная веб-версия https://hd.kinopoisk.ru/ |
| VK Видео | Веб-версия https://vkvideo.ru/ |
| FitStars | Веб-версия https://fitstars.ru/ |
| Lampa | Веб-приложение https://lampa.mx/ внутри перехода MSX |
| Zona | Информационная панель и ссылка на официальный сайт; запуск на webOS не подтверждён |
| DORMI | Информационная заглушка, адрес ещё не задан |

Ни один непроверенный app ID не используется. link:window не означает запуск установленного приложения.
На реальном LG ещё нужно проверить открытие сайтов, вход, воспроизведение и возврат; они зависят от версии webOS, сети, региона и подписки.
Lampa — клиент; меню не устанавливает источники, плагины или серверы. Доступность её внешнего адреса также требует проверки на ТВ.
Каталог не сканирует установленные приложения LG. Root и Developer Mode не нужны.

## Добавление приложения
Добавьте объект в all-apps.json → pages[0].items (либо новую страницу при заполнении сетки).
Для главного экрана добавьте/замените объект в menu.json → menu[0].data.pages[0].items.
Поля: id (уникальный), type, layout (целые x,y,w,h в сетке 12×6), title, titleFooter, icon, color, action.
Сайты используют link:window:https://..., TV web apps могут использовать link:https://...
Для нативного приложения сначала подтвердите фактический ID именно установленной версии на LG; документированный синтаксис — system:lg:launch:APP_ID. Не подставляйте Android package name или числовой ID страницы магазина без проверки.
Не допускайте пересечения интерактивных плиток. Все URL абсолютные HTTPS.

## Документация, проверена 21.10.2026
- [Menu Root](https://msx.benzac.de/wiki/index.php?title=Menu_Root_Object), [Menu Item](https://msx.benzac.de/wiki/index.php?title=Menu_Item_Object)
- [Content Item / grid](https://msx.benzac.de/wiki/index.php?title=Content_Item_Object), [Colors](https://msx.benzac.de/wiki/index.php?title=Colors)
- [Actions](https://msx.benzac.de/wiki/index.php?title=Actions), [External apps](https://msx.benzac.de/wiki/index.php?title=Tips_%26_Tricks#External_Platform_Games/Apps)
- [Start setup](https://msx.benzac.de/wiki/index.php?title=Setup_Start_Parameter)
- [Lampa source](https://github.com/yumata/lampa), [Zona](https://zona.ru/)

Дизайн использует штатные элементы MSX, без тяжёлого стороннего интерфейса. Скругление зависит от настройки стиля MSX.
