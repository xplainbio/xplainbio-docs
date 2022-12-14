# Начало работы

## Регистрация

Для начала работы с платформой XplainBio необходимо пройти регистрацию в системе. Для этого нажмите на надпись "Аккаунт" на главной странице сайта:

<div class="img" align="center">

![Account](/assets/account.png)
</div>

Далее нажмите на надпись "Зарегистрироваться" и введите свой е-мейл и желаемый пароль:

<div class="img" align="center">

![Registration](/assets/register.png)
</div>

При успешной регистрации на указанный е-мейл придет ссылка для активации учетной записи (письмо может придти в спам). Активируйте учетную запись с помощью ссылки.

## Создание проекта

После активации учетной записи войдите в систему, используя е-мейл и пароль. При первом входе главная страница представляет собой пустую страницу проектов &ndash; для начала работы создайте свой первый проект, нажав на кнопку "Добавить проект":

<div class="img" align="center">

![Init](/assets/init.png)
</div>

Введите название проекта, выберете базы мутаций (можно оставить пустым) и панель для анализа (соответствует применяемой тест-системе):

<div class="img" align="center">

![Init](/assets/new_project.png)
</div>

После создания проекта можно начинать [загрузку файлов](upload.md).

## Концепции

* Проект &ndash; группа образцов, объединеных общим признаком (запуск на приборе, заболевание, панель генов и т.д.)

* Образец &ndash; набор данных, относящихся к одной единице анализа (файлы FASTQ, параметры качества, аннотированная таблица вариантов, патогенные мутации, отчет)

* База мутаций &ndash; таблица мутаций с указанием патогенности, может быть публичной или приватной. При подключении к проекту служит источником аннотации для вариантов образца. Присутствующие в базе мутаций строки образца отмечаются цветом, соответствующим классу патогенности или классу клинической значимости. Приватные базы мутаций наполняются пользователем и являются внутрилабораторным хранилищем информации о классификации обнаруженных вариантов.

* Фенотип &ndash; вспомогательный признак образца, например, РМЖ, РЯ или рак простаты.

* Панель &ndash; список геномных регионов и генов, используемый при поиске нуклеотидных вариантов в образце, а также настройки критериев автоматического включения вариантов в отчеты.

* Анализ герминальных мутаций &ndash; метод поиска нуклеотидных вариантов с использованием в качестве основного инструмента GATK4 HaplotypeCaller и в качестве дополнительных Strelka2 и DRAGEN. 

* Анализ соматических мутаций &ndash; метод поиска нуклеотидных вариантов с использованием в качестве основного инструмента GATK4 Mutect2 и в качестве дополнительных Strelka2 и DRAGEN для поиска потенциально пропущенных герминальных мутаций. 

* Тип анализа зонды &ndash; используется для методов подготовки библиотек на основе гибридизационных технологий (Roche KAPA HyperCap, Agilent SureSelect, IDT xGen Hyb).

* Тип анализа ампликоны &ndash; используется для методов подготовки библиотек на основе амплификационных технологий (Thermo AmpliSeq), в этом случае отключается маркировка дубликатов.

* Отчет &ndash; файл формата DOCX, содержащий информацию о проведенном анализе, метриках качества, выбранных патогенных мутациях, генерируется на основе индивидуальных настраивамых шаблонов.