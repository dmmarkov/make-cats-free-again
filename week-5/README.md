# Спасибо!

Огромное спасибо за курс!!!

Мне понравился весь материал. Я с огромным удовольствие читал всё! (кроме доп.литературы, ведь её надо читать после окончания курса =D )

Я взглянул на проектирование системы совсем под другим углом. У меня было какое-то понимание что вот это делать вот так, а это как-то так, потому что в прошлый раз делал так и было совсем не очень, но не было цельной картины. Теперь у меня со скрежетом двигаются шестерёнки в какую-то новую реальность, которая более цельная =)

Раньше мне было непонятно какие артефакты оставлять, чтобы потом не было мучительно больно разбираться с проектом, особенно в случаях когда проект делали, потом переключились куда-то на 3-6-9 месяцев, а потом вернулись к нему. Сейчас есть новые знания, которые очень хочется применить на практике и в ближайшее время начну внедрять какие-то идеи. И буду защищать эти идеи, потому что они работают =)

В общем, куда бы не завела меня кривая дорога жизни, то чувствую, что знания, полученные на курсе, совсем не лишние и помогут мне в будущем.

# Сравнение 0 ДЗ и 3 ДЗ

0 ДЗ: https://github.com/dmmarkov/make-cats-free-again/tree/main/week-0

3 ДЗ: https://github.com/dmmarkov/make-cats-free-again/tree/main/week-3

На мой взгляд сравнить 0 ДЗ и 3 ДЗ с ходу очень сложно =)

Когда делал 4 ДЗ, то уже стало понятно, что в 0 ДЗ мало что понятно. Есть какие-то лишние детали, непонятно что где и зачем, хотя когда делал 0 домашку, то казалось что ну в целом оно как-то же логично и понятно.

А по факту в ходе выполнения 4 ДЗ https://github.com/dmmarkov/make-cats-free-again/tree/main/week-4 пришлось переделывать схему из 0 домашки, чтобы было понятно с какой системой я работаю и к какому виду я пытаюсь её привести.

В ходе выполнения 4 домашки я обнаружил, что в 0 домашке у меня оказался один такой мега-сервис, где смешались 3 сущности + 1 технический шаг из биллинга. Обнаружить кусочек биллинга - это прям вообще было что-то такое неожиданное =) Моя логика была такой - раз нужно менеджерам, то это какая-то там админка для них и там вот это всё будет. Как же я ошибался ¯\_(ツ)_/¯

Отдельно мне понравилась идея, что биллинги должны быть раздельными, потому что они для разных бизнес-процессов и не надо их смешивать. Неожиданно в 0 домашке я даже разделил их (правда они как бы в 1 сервисе с заказами), а когда делал 1 ДЗ уже даже не вспомнил об этом `¯\_(ツ)_/¯`. Но это, скорее всего, связано с тем, что я старался не думать о 0 домашке, а старался делать то, что было в ДЗ урока и делать так как описано в уроке.

Мне очень понравился подход в курсе о том что нужно сделать, чтобы спроектировать и описать систему, которая будет нормально работать. Это касается всего, начиная от ES заканчивая просто верхреуровневой схемой сервисов.

Я раньше пытался понять что же надо такое оставить в виде артефакта, чтобы было понятно что, зачем и почему, а оказывается нужен целый набор артефактов.  Вот этот скоуп артефактов мне очень нравится. Чутка бесит рисовать в Miro, но я подберу себе удобный инструмент на досуге =)

# Идеи и подходы, которые я хотел бы внедрить в проектах

Если честно, то хочется всего и сразу =) Вот просто взять все наработки и начать по ним работать, но я знаю что меня не поймут, да и я не такой, чтобы прям вот прийти и сказать "всё херня, завтра работаем по новому!"

Первое что хочется опробовать - это ES. И я уже даже задавал вопрос на тему Event Storming в чате. Даже чуть-чуть попробовал. На первый взгляд, мне показалось, что больше похоже, что в моём случае нужно что-то другое. Возможно Data-Modelling будет даже лучше, потому что в контексте текущих задач он прям показывает где у меня entity и почему у меня в проекте местами распределённый монолит.

Если в виде списка оформить, то вот такой список чего бы я хотел внедрить:
1. Самое главное чего мне не хватало - это ADR. У нас исторически повелось, что главные носители знаний - это люди. Я честно как-то пару раз пытался выгружать знания, но было это как-то так себе. В виде текста вообще мало кто читает и пытается разбираться. В виде видео - опять же выгрузка постфактум, которая работает, но это долго сложно и не всегда нужно. Работающей версией оказалось рисование дизайна по которому имплементируем, но это не совсем то, потому что в дизайне уже сказано что делать, но нет ответа на вопрос "почему".
2. Data-Modelling - у нас вагон и маленькая тележка данных + они ещё и размазаны по системе. Как-то в рамках 1 или 2 сервисов коллега предложил начать со схемы данных, но сделали в варианте хардкорного рисования со всеми связями и неймингом. Конечно такой подход никто не оценил.
3. Верхнеуровневая схема коммуникаций сервисов. Мне кажется если сделать картинки как в уроке, то возможно получится показать коллеггам, что некоторые сервисы вообще не нужны, а некоторые имеют ошибочные связи, поэтому мы будем переделывать эти сервисы.
4. Составить план работы над проектом, как описано в 4 уроке. Это вот прям то, чего не хватает сейчас, потому что прям заметно иногда, что кроме меня мало кто знает следующий шаг, хотя периодически мы всё это проговариваем. Но визуализация - это прям топчик. Лично мне хотелось бы к этому как-то прикрутить визуализацию-автоматизацию, чтобы было видно, что эти задачи к этому квадрату, какой прогресс и т.д.
5. Хочется правильно поработать с требованиями. У нас их как-то пытались переваривать, но там больше была история про то, что их надо разложить по корзинам "требования безопасности", "требования к мониторингу", "требования к чему-то там ещё" (я просто забыл как корзины называются, но их там штук 5 было `¯\_(ツ)_/¯`). Естественно эта работа с требованиями никак не помогает проекту.
6. Хочу нормально спроектировать и описать систему, а потом начать над ней работать. Если честно, то тут меня вперёд двигают знания сразу с нескольких курсов, которые собираются в цельную картину "как делать надо", "как надо защищать свои границы" и "как надо продавать свои идеи". В общем тут сложно, но очень хочется начать делать нормально =)
