# notcoin
**Бот на Басе, для игры в НОТКОИН**

Написал: @hvrsh  (TG)

Канал: @hashvers    (TG)
#
Инициализация аккаунтов - через браузерную эмуляцию(чтобы получить нужное auth инфо)

Игра - на запросах


Для начла запускаемся в режиме Data instalator чтобы поднять все нужные вам аккаунты.

Важно! Аккаунт должнен иметь юзернейм, и активный диалог с ботом Ноткоина(хотя бы переход по рефке, чтобы скрипт мог открыть окно игры для забора даты.)

Тоесть в режиме Data instalator выбираем колово аккаов которое хотим инициализировать, и количество потоков сколько одновременно бразуеров запускать (пример 25 аккаунтов, потоков 5). И у вас всегда будет открыто одновременно не больше 5 браузеорв для прогона всех 25 аккаов. Прокси будут браться построчно в зависимости от порядка браузера, в дальнейшем после инициализации эти же прокси будут использоваться для игры через запросы, бинд автоматический.
Тоесть тут наша задача залогинится в аккаунты(не убирать галку сохранить на этом комютере вход!) в барузерах, и передать  ему управление после этого, дальше он все что надо сделаает и закроет его. так нужно пройтись по всех браузерах\аккаунтах.

После это как все проделано для того чтобы играть запускаемся в режиме **Gamer**. На основе данных что были собраны в первом моде, он начнет игру на запросах для каждого аккаунта многопоточно(25 аккаунтов инициализировали\25 потоков игры). Дата которую мы собрали в первом модуле имеет свойство терять актуальность (Каждые 2 часа). Тогда скрипт сам поднимет бразуер того акканута где дата не актуальна пересоберет новю дату(ваше участие уже не надо т.к. бразуера и логины сохранились с первого запуска инициализации) и продолжит игру за запросах.

Запросы отправляются грамотно. С учетом соответствующих реальной игре задержек.

# VER 1.1

Проделан огромный пласт роботы, скрипт неплохо оттестирован, и должен работать хорошо(с хорошими расходниками тг, прокси)

**Добавлено:**

**Gamer** - в режиме появиалсь проверка на дейли квесты, автоматическое их выполнение при наличи, также появилась ловля фри турбобустов (практически не появляются только в самом начале акка).

Добавлено режим **Buyer** с помощю него можно купить нужные вам айтемы на акканутах. Для того чтобы их купить нужно заполнить файлик *buy_list.csv* (появится после первго прогона в режиме **Gamer**), это табличка в текстовом формате csv, по умолчанию скрипт заполнит ее значениями "один", что соответствет разовой попытке покупки соответствующего буста, если не хотите что-то покупать указываете 0, елси хотите больше одной покупки то дургую цифру, например 3. Удобнее всего такой файл редактировать через Excel там он откроется как обчыная табличка.

В процесе игры стата аккаунтов будет логироваться в файлик *accounts_info.csv*, по нему можно ориентироваться что и где нужно докупить. Также уддобно смотреть открывая его через Excel.

# VER 1.2

Попытлася максимально отфиксить пред. версию.

**Добавлено:**

**Proxy Renew** - в этом режиме вы сможете обновить прокси в ваших аккаунтах. Можно обновить как в Бразуере или Плеере по отдельности, так и всё в месте, для этого выбираем соответствющий, параметр где нужно обновить. Прокси для обновления будут браться с файла *proxies.txt* построчно.

**Daily Task Check** - можно отключить чекер дейли таксов и их выполнение, елсив вам это нужно.

**Try claim onboarding task** - пробовать ли заклеймить онбординг таски (за лиги, первые 1000 коинов, сквад).

# VER 1.3

Наличее версии обсусловлено тем, что в недавнем времени ноткоин накинул на запросы доп защиту и все запросы перестали проходить. Т.к штатными методами баса не удалось оправить запросы должного качества, для работы бота нужны дополнительные аддоны\приготовления для успешной работы софта.

1. Устанавливаем GoLang https://go.dev/dl/ (go1.21.6.windows-amd64.msi).
2. Скачиваем сам репозиторий с скриптом.
3. Заходим в папку *TLS-Fingerprint-API-main*, в строке поисковика вбиваем команду **cmd** для того чтобы открыть терминал из под этой папки.
4. Вводим команду **go run .** . Эта команда запустит локальный сервер через который будут проходить наши запросы, терминал не закрывать во время работы скрипта!
5. Можем запускать сам скрипт.

**ВАЖНО!**
Поменялся формат проски. Теперь можно указывать прокси только в таком формате - `http://user:pass@host:port`.
Если вы уже до это работали с софтом, то можете сменить формат на новый через функцию **Proxy Renew**, это нужно сделать для Gamer-а обязательно, для браузера можете оставить так как и было.

