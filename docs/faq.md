# Частые вопросы

### Какие требования к загружаемым файлам FASTQ?

Для платформы Illumina (этот тип анализа также совместим с BGI/MGI) обязательно наличие не менее одной пары файлов парноконцевых прочтений *.fastq.gz на образец с одинаковым количеством записей в каждом файле. Не рекомендуется перед загрузкой обрабатывать файлы с прибора любыми инструментами, способными изменить число прочтений &ndash; Trimmomatic, cutadapt  и др.

### Существуют ли ограничения на размер файлов?

Ограничений нет, сервис тестировался на размерах входных файлов до 300 Гб, объем загружаемых данных ограничивается только скоростью и надежностью интернет-соединения, рекомендуется использовать стабильный канал не менее 100 Мб/сек. В случае использования Wi-Fi возможны обрывы соединения и остановка процесса передачи, в этом случае следует повторить загрузку недозагруженных файлов.

### У меня восемь FASTQ-файлов одного образца с четырех дорожек, необходимо ли их склеивать перед загрузкой?

Нет, сервис позволяет прикрепить к образцу несколько наборов FASTQ-файлов, необходимо только внимательно следить за правильным расположением прямых и обратных ридов (R1 и R2) в парах файлов.

### Как автоматизировать создание образцов из FASTQ-файлов?

В сервисе предусмотрена возможность автоматической группировки файлов, принадлежащих одному образцу &ndash; для этого они должны иметь стандартный для приборов Illumina [шаблон имени](https://support.illumina.com/help/BaseSpace_OLH_009008/Content/Source/Informatics/BS/NamingConvention_FASTQ-files-swBS.htm), например:
D3094_S15_L001_R1_001.fastq.gz
D3094_S15_L001_R2_001.fastq.gz,
где D3094 &ndash; имя образца, S15 &ndash; номер образца внутри запуска прибора, L001 &ndash; номер дорожки, R1 &ndash; прямые риды, R2 &ndash; обратные риды.
Если файлы для образца будут иметь соответствующие шаблону имена, то они при загрузке автоматически будут объединены в одну группу, из которой можно легко создать образец с правильно расставленными дорожками.

### У меня FASTQ-файлы одного образца с разных запусков разных приборов, как их обработать?

Не рекомендуется вручную объединять перед обработкой данные с разных запусков или с разных дорожек в одну пару файлов, в нашем сервисе есть возможность привязки более двух файлов к одному образцу. Это ускоряет обработку, так как каждая пара FASTQ-файлов обрабатывается независимо от других, а модель BQSR учитывает особенности каждого прибора/дорожки, что повышает качество анализа. Данные объединяются автоматически перед этапом поиска вариантов.

### Какой версией геномной сборки предпочтительнее пользоваться - hg19 или hg38?

Максимальную точность в детекции мутаций обеспечивает hg38, но после получения VCF требуется еще этап аннотаций, а на нем определяющую роль играет версия генома баз данных, используемых в качестве источников. Например, сборка hg38 для ряда баз (gnomAD 2.1.1, InterVar) доступна только в виде лифтовера, что может приводить к редким (но все же вероятным) ошибочным аннотациям. Основная часть информации по клинически значимым мутациям в первоначальном виде тоже была получена для сборки hg19 (например, HGMD). Поэтому однозначного ответа на этот вопрос не существует, все определяется задачами и накопленным в лаборатории опытом интерпретации. Мы рекомендуем иcпользовать hg38.

### В чем отличия анализа полного генома?

При поиске SNP и INDEL в полных геномах мы используем специальные версии референсных последовательностей и геномных интервалов, в которых замаскированы или исключены некоторые участки хромосом, затрудняющие поиск вариантов &ndash; центромеры, крупные повторы, псевдоаутосомные области половых хромосом. Это позволяет избежать ошибок и ускоряет работу GATK. Скачать файлы регионов для ознакомления можно по ссылке.

### Почему доступен только анализ по поиску мутаций?

Наша система нацелена на решение одной задачи &ndash; минимизацию времени обработки большого количества образцов с одновременным сохранением высокого качества анализа. Данная проблема пока что существует только в области определения наличия мутаций в образцах при наследственных заболеваниях, назначении таргетной терапии и т.д. Открытая модульная архитектура системы позволяет при необходимости с легкостью добавить анализ микробиома, метилома, экспрессии мРНК и микроРНК под потребности конкретного заказчика.

### Почему значения в столбцах "Функция" и "Локализация" иногда не соответствуют наблюдаемой замене?

В случае сложных инсерций или делеций (например, c.8753_8761+39delTATCCACAGGTCACGCCACTCCTCTTCTTGTCACCGACGCTTCCTCAG) альтернативный аллель может иметь несколько функционально значимых отличий от референсного. Чтобы не перегружать таблицу избыточным текстом, в столбце "Функция" показывается только наиболее важный с точки зрения влияния на текущий транскрипт эффект замены. В вышеупомянутом примере для транскрипта NM_001322468.1 из нескольких аннотаций (нарушение сайта сплайсинга, делеция без сдвига рамки считывания, замена в интроне) для отображения выбирается "splicing", так как на уровне генома эта делеция затрагивает границу интрона/экзона в гене MUC4, хотя на уровне белка замена выглядит как  p.Val2918_Thr2920del.

### Что означает альтернативный аллель "*" в VCF и таблице?

В спецификации VCF это значение зарезервировано для вариантов, которые не могут быть определены из-за того, что их позицию перекрывает другая делеция. Как правило, такие точки требуют визуального контроля в геномном браузере. Подробнее можно прочитать [здесь](https://software.broadinstitute.org/gatk/documentation/article?id=11029).

### Почему для вариантов с низким покрытием часто отображается только фильтр LowDP?

Для экзомов и таргетных панелей в регионах с покрытием менее 10х методы фильтрации не позволяют надежно различать истинно- и ложноположительные варианты, поэтому информация о значениях других метрик бесполезна. Следует с большой осторожностью принимать решение по таким точкам, при необходимости либо переделывая анализ, либо проверяя нуклеотидную замену альтернативным методом.