# BetterDiscord-Animated-Status

<!-- vim-markdown-toc GFM -->

* [установки](#установки)
* [Применение](#Применение)
* [Тайм-аут / время для ключевого кадра](#Тайм-аут-/-время-для-ключевого-кадра)
* ['богатый' против 'сырого' редактора](#богатый-против-сырого-редактора)
* [Анимации](#Анимации)
* [Примеры](#Примеры)
* [Discord Nitro Emoji](#discord-nitro-emoji)
	* [Пользовательский Javascript](#Пользовательский Javascript)

<!-- vim-markdown-toc -->

## установки
Установить [BetterDiscord](https://github.com/rauenzi/BetterDiscordApp)\
Загрузите  [animated-status.plugin.js](/animated-status.plugin.js?raw=true) в следующий каталог\
Mac: `~/Library/Preferences/BetterDiscord`\
Windows: `%appdata%\BetterDiscord\plugins`\
Linux: `~/.config/BetterDiscord/plugins`

## Применение
Откройте Discord, перейдите в Настройки \> Плагины, включите AnimatedStatus и нажмите Настройки. \
Введите необходимую информацию в поля ввода и нажмите «сохранить».
## Тайм-аут / время для ключевого кадра
Значение определяет длину каждого шага анимации в миллисекундах.
Пример: с таймаутом 2000, следующая анимация займет 4 секунды.
```
"abc"
"def"
```
o предотвратить рассылку спама на сервере Discord запросов, минимальный допустимый тайм-аут жестко задан равным 2,9 секунды. \
По логике, время ожидания анимации должно быть не менее 2900, в лучшем случае 10000 миллисекунд (10 секунд), чтобы анимация выглядела гладко на других клиентах. \
В мобильном приложении статус обновляется непостоянно, т.е. список участников сервера обновляется на основе действий пользователей в приложении. Не удивляйтесь, если анимация не будет плавной или будет пропускать кадры. \
^ Согласно [@pintoso](https://github.com/pintoso)

## 'богатый' против 'сырого' редактора
Начиная с последней версии, плагин теперь имеет новый многофункциональный редактор. Это не добавляет функциональности, но значительно упрощает редактирование анимации! \
![Rich Editor](/screenshots/rich.png?raw=true)\
Необработанный редактор - это просто поле ввода текста, в котором вы можете вручную редактировать анимацию в формате, подобном json \
(глядя на исходный код, видно, что это в основном json с отсутствующими скобками)
## Анимации
![Settings Page](/screenshots/settings.png?raw=true)\
Анимации выполнены в очень простом и понятном синтаксисе.
```
"Test (Message)"
"Test (Message)", "👍 (Symbol)"
"Test (Message)", "emoji (Nitro Symbol)", "000000000000000000 (Nitro Symbol ID)"
"eval new String('test') (Javascript)"
"eval new String('test') (Javascript)", "eval new String('👍') (Javascript)"
...
```
## Примеры
Текст переключения:
```
"Text 1"
"Text 2 with emoji", "👍"
```

## Discord Nitro Emoji
- Open a discord Chat, type `\`.
<img src="screenshots/nitro0.png">
- Select the emoji you want to include in your status using the emoji picker.
<img src="screenshots/nitro1.png">
- Notice that the message changed to `<:emojiname:emojiid>`. The values inside the brackets (emojiname and emojiid) are the values required for the status.
<img src="screenshots/nitro2.png">
- Edit the settings accordingly
<img src="screenshots/nitro3.png">

### Пользовательский Javascript
Have the current time as your status:
```
"eval let fmt=t=>(t<10?'0':'')+t;let d=new Date();`${fmt(d.getHours())}:${fmt(d.getMinutes())}:${fmt(d.getSeconds())}`;"
```

Have the current time with the corresponding clock symbol as your current status
![Settings Page](/screenshots/status_clock.png?raw=true)
```
"eval let fmt=t=>(t<10?'0':'')+t;let d=new Date();`${fmt(d.getHours())}:${fmt(d.getMinutes())}:${fmt(d.getSeconds())}`;", "eval ['🕛','🕐','🕑','🕒','🕓','🕔','🕕','🕖','🕗','🕘','🕙','🕚'][((new Date()).getHours()%12)];"
```
