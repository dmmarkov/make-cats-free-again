# Event Storming

Ссылка на ES модель https://miro.com/app/board/uXjVMI_dFvQ=/?share_link_id=594646212104

# Логика по которой сгруппировали команды и события в контексты

Я смотрел на то вокруг чего всё крутится.

В блоке заказы у меня всё крутится вокруг того, чтобы создать заказ, потом назначился воркер, обработался заказ.

Расходники - это отдельный отдел со своими процессами, поэтому их в отдельный контекст.

Аудит заказов - всё крутится вокруг того что надо взять какой-то завершённый заказ и по нему отработать. Там 2 flow, т.к. есть некоторые отличия по отработке провального и успешного заказа. Чисто в теории каждый из flow также может меняться.

Пул воркеров собран в одном месте, потому что все действия направлены на то, чтобы сформировать этот самый пул.

Ставки - это отдельная побочная штука, которая живёт сама по себе

Платежи вынесены в отдельный контекст, потому что сам по себе механизм не завязан на какие-то другие процессы. Для выполнения платежей необходимо получить информацию о заказах их стоимости для клиента, а для воркера узнать сколько ему начислено за тот или иной заказ. Эта информация будет находиться в контексте заказов, а здесь она нужна, чтобы сформировать отчёт-инвойс, по которому выполняется оплата.

Матчинг воркеров - это что-то закрытое, поэтому это какой-то дополнительный контекст, который как-то живёт и мы можем на него немного влиять изменяя шаги

# Модель данных

На модели подписаны только стрелки has many

Не подписанные стрелки считаются has one

Ссылка на модель данных https://miro.com/app/board/uXjVMINkFRc=/?share_link_id=159716328779

# Модель коммуникаций в системе
Считаем, что каждый контекст - это отдельный сервис

Все сервисы общаются между собой асинхронно, за исключением взаимодействия  заказов и матчинга. Результат матчинга нужен сразу, потому что после него нужно сразу выполнять ряд следующих действий.

Остальные сервисы могут общаться асинхронно.

На схеме модели данных пунктирными стрелками показано какими данными обмениваются сервисы.

Отдельным цветом показан владелец данных

# Реализация проекта

Для простоты разработки каждый контекст - это отдельный сервис.

Всё сваливать в монолит не хочется, т.к. ряд логики совсем не зависит от другой.

В текущем варианте получает компромисный вариант, что есть некий укрупнённый сервис, который потом при необходимости можно разбить или оставить как есть, если всё будет работать.

Все сервисы общаются между собой асинхронно, за исключением взаимодействия  заказов и матчинга. Результат матчинга нужен сразу, потому что после него нужно сразу выполнять ряд следующих действий.

Остальные сервисы могут общаться асинхронно, потому что нет необходимости в мгновенной реакции.

# Спорные места
В целом делал первый раз и кажется я что-то слишком подробно сделал, а что-то для меня непонятно, потому что я ни разу не работал с чем-то похожим =)

Непонятно что делать с продуктовыми гипотезами. Я их положил в аудит, потому что они там порождаются, поэтому пусть там пока и лежат

А ещё я много деталей упустил на схеме, которые потом могут оказаться не понятными для разработчиков

Не понятно как считать с отделом расходников. Мы ими управляем или нет? Если да, то надо тогда целую складскую логику делать с дозаказом.

Не понял как рисовать внешнюю систему в рамках контекста. Нарисовал как понял.

Очень сильно разбежались заказы. Они почти везде есть. Не уверен, что это правильно вот так, но мне кажется изоляция заказа и его аудита - это гуд.

Вопросы было  уже некогда спрашивать, потому что всё в последний момент =(
