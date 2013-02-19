RutubePlayerJSAPI
=================

Общий принцип работы полностью схож с принципом работы YouTube-плеера ( повторил функциональность для более простого встраивания другими сайтами ).

Для использования JS-вызовов необходимо *предварительно* сообщить плееру о заинтересованности испольозвания JS-API плеера, иначе эта функциональность будет отключена.

При создании объекта плеера на странице передать во FlashVariables параметры:

- **playerId** - идентификатор плеера, для внуреннего использования, в случае если на странице присутствует несколько плееров
- **initJsCallback**- имя метода, который вызывает плеер для оповещения скриптов о полной загрузке и доступности вызова методов плеера (*callback на первичную готовность плеера*).
- **stateJsCallback** - имя метода, который вызывает плеер для оповещения скриптов при смене состояния плеера (*callback при каждой смене состояния плеера*).
- **errorJsCallback** - имя метода, который вызывает плеер для оповещения скриптов при ошибке (*callback в случае ошибки плеера*).
- **playbackCompleteJsCallback** - имя метода, который вызывает плеер для оповещения скриптов об окончании проигрывания текущего ролика (*callback на оповещение проигрывания ролика*).

Например:

```
<param name="flashVars" value="initJsCallback=window.playerAdapter.onready&amp;
stateJsCallback=window.playerAdapter.changeState&amp;
errorJsCallback=window.playerAdapter.errorState&amp;
playbackCompleteJsCallback=window.playerAdapter.playComplete">
```


####Поддерживаемые плеером методы.

Метод | Описание | Передаваемые параметры | Возвращаемые параметры |
------------ | ------------- | ------------ |------------ |
isAvalible| возвращает доступен ли плеер или нет | |Boolean |
cleanHeap| принудительно вызывает сборщик мусора у плеера | | |
playVideo| запуск проигрывания видео | | |
pauseVideo| остановка на паузу проигрываемого видео | | |
stopVideo| остановка проигрываемого видео | | |
seekTo| перемотка видео на заданную позицию, в секундах | позиция в секундах | |
canPlay| может ли плеер проиграть загруженный контент | | Boolean |
loadVideoByHash| загрузить видео, передав в качестве параметра хеш ролика | хеш ролика, строка | |
isLoaded| проверить, загружен ли ролик в плеер или нет | | Boolean |
isCompleted| свойство позволяет проверить завершилось ли проигрывание ролика | | |
getMetaInfo| получить метаинформацию о ролика, в формате JSON. временно недоступно | | Объект в виде JSON |
mute| выключить звук | | |
unMute| включить звук | | |
isMuted| выключен ли звук | | Boolean |
setVolume| установить уровень звука | целое число, от 0 до 100 | |
getVolume| получить уровень звука | | целое число, от 0 до 100 |
getCurrentTime| текущее время проигрывания | | дробное число |
getDuration| длительность проигрываемого ролика | | дробное число |
getPlayerState| получить текущее состояние плеера ( playing, paused, stopped, loading ) | | строка-состояние плеера |
addListeners| добавление методов обратного вызова для получения обратной связи от плеера. Передается объект со свойствами ,в которых строками указаны методы обратного вызова. | error, playerState | Boolean |


####Возможные состояния плеера

Состояние | Описание |
----|-----|
uninitialized |Плеер неинициализирован. Нет проигрываемого контента. |
loading|Контент загружается в плеер|
ready|Плеер готов к произгрыванию загруженного контента.|
playing|Проигрывание|
paused|Плеер на паузе|
buffering|Буфферизирование|
playbackError|Ошибка проигрывания|


 
 
 
 
