---
title: "Скорость"
date: 2019-12-01T11:04:57+02:00
lastmod: 2019-12-01T11:04:57+02:00
tags: ["work"]
---

Скорость сборки, как и интерактивность — еще одна, к моему прискорбию, недооцененная характеристика платформ, сред, языков.

Мозги так устроены, что дай им малейший шанс отлынивать от работы — моментально этим воспользуются. Все знают анекдот про "у меня код компилируется"? Вот то-то же. Сборка, компиляция, редеплой, называйте как хотите — всё это убивает эффективность разработчика, снижает каденс (загуглите что это такое), притупляет мысль. На простейшие вещи уходит куча времени. В частности именно поэтому я не люблю мобильную разработку — пока дождешься сборки, пока она доедет на девайс, пока перезапустится приложение — пройдет вечность, а мозг в это время уже переключился на просмотр котиков и SJW-срачей в твиторе, все, фокус потерян, поток теперь не мощная горная река сметающая когнитивной силой всё на своём пути, а жалкий ручеёк, медленно пересыхающий с каждым просмотренным постом в соцмедиа.

Из двух платформ я бы выбрал ту, что дает большую скорость отклика (неважно будет там сборка или не будет). Поэтому в своё время (2016) у меня люто бомбануло от Scala — там сборка была настолько медленной, что разрабатывать что-либо совершенно не было никакого желания, несмотря на все плюшки с сахарной пудрой. Сейчас-то может быть дела получше, но возвращаться желания нет.

Лучше всего, конечно же, ничего не собирать. Написал, нажал кнопку (а то и без нажатия), и оно сразу выполнилось и показало результат. Нет времени на котиков, результат уже готов господин программист, извольте провалидировать!

Интересно, что некоторые редакторы заставляют пользователя явно сохранять файл. IntelliJ например по-умолчанию включает автосохранение, и вообще не надо думать о такой вещи как файловая система. Написал — и оно сразу сохранилось. Почему некоторые другие редакторы, хотя и имеют такую опцию, всё равно требуют нажатия Ctrl+S, мне непонятно.

Поэтому так ценны хорошие (и не только) REPLы, которые являются ничем иным как бесконечной дебаг сессией, где код меняется, перегружается, выполняется мгновенно, не давая мозгу отвлекаться, держат фокус и дают моментально проверять свои гипотезы, писать небольшие кусочки для набросков скелета программы, убедиться что работа идет в правильном направлении, пройти позитивный сценарий и дальше — раз! — и одним махом написать решение для искомой проблемы.

Среда разработки с кодом должна быть как паровоз, несущийся сквозь Сибирь, а вы — как машинист, на ходу ковыряющийся в движке, меняющий состав угля и всякие хитрые рабочие параметры, немедленно сказывающиеся на результате.

## PHP

Знаете, какой один из пунктов глумления над PHP разработкой часто можно услышать? 

"...А деплоят они через синхронизацию локальной папки по FTP, прикинь, га-га-га". Покурили, посмеялись, и пошли такие гордые дальше писать километровые helm-чарты на шаблонизированном YAML для своих кубернетесов. 

Этим продуктам жизнедеятельности современных инфраструктурных практик невдомёк, что PHP разработчик, закидывающий свои фиксы по FTP, находится на световые годы впереди по скорости доставки своих изменений бизнесу. Приходишь на конференцию послушать очередного все понявшего инженера, а он и говорит "в начале мы деплоили через git pull (тут такой стыдливый смешок), потом собирали deb-пакеты и раскатывали через ansible, а теперь у нас blue-green-canary-zero-downtime deployment в service mesh на k8s кластере" представляя это как будто что-то хорошее и прогресс. 

А вот нифига это не прогресс, братец, это регресс, да еще и какой серьезный, это откат во времена перфокарт и компьютерного времени по расписанию.

Люди уже и позабыли, что вовсе необязательно собирать контейнеры, закидывать это все в какие-то кластера, разворачивать реплики, что можно просто сделать git pull и в секунду zero-downtime задеплоить своё решение. 

Я конечно сильно утрирую и и гиперболизирую, все эти контейнеры не просто так придумали, но знаете в чем преимущество PHP над всеми остальными платформами? Программист не ждет. Он просто написал строку, нажал "обновить" в браузере и у него все работает. Его код подхватывается моментально, сразу же. Без ожиданий, тут же, на месте. И в этом сила PHP. Пока другие пересобирают артефакты, редеплоят контейнеры и перепаковывают бандлы, PHP программист уже нафигачил кучу функциональности. И деплоят в одну секунду. Без даунтайма.

Миграции баз данных, конфигурации и прочие штуки которые разрушают состояние, сильно портят жизнь, но всего этого не так много и в основном можно спокойно писать код в редакторе моментально получая результат.

Если бы не было Ruby on Rails, я бы на PHP писал, вот вам крест на всё пузо! И ничего что там переменные с $ надо начинать и много легаси осталось, и состояния нет, и curl надо вызывать системный, все это перекрывается скоростью.

В любом языке или платформе я сразу ищу способы всяких хотсвапов, лайврелоадов и прочих редеплоев чтобы не ждать пока компилируется.

Говорят в Erlang/OTP вообще можно в рантайме код менять как-то хитро без ребутов и прочей ерунды. Но это не точно, а чтобы убедиться самому руки никак не доходят.