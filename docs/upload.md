# Загрузка файлов

Загрузка осуществляется в облачное хранилище без лимитов на размер файлов, объем загружаемых данных ограничивается только скоростью и надежностью интернет-соединения, рекомендуется использовать стабильный канал не менее 100 Мб/сек. В случае использования Wi-Fi или ненадежного канала связи лучше загружать каждый образец отдельно, так как возможны обрывы соединения и остановка процесса передачи, в этом случае придется повторить загрузку всех недозагруженных файлов.

Если комплект FASTQ-файлов (например, полный запуск с прибора) имеет стандартный для приборов Illumina [шаблон имени](https://support.illumina.com/help/BaseSpace_OLH_009008/Content/Source/Informatics/BS/NamingConvention_FASTQ-files-swBS.htm), то наиболее быстро и удобно запустить обработку следующим образом:

1. После [создания](start.md) первого проекта откройте менеджер загрузки из разделов "Проекты" или "Файлы". Для загрузки файлов только в один проект зайдите в него и нажмите "Загрузить файлы".
<div class="img" align="center">
<img src="https://github.com/xplainbio/xplainbio-docs/raw/gh-pages/docs/assets/open_file_manager.png"></img>
</div>

<div class="img" align="center">

![Pipeline](/assets/open_file_manager.png)

</div>


2. Перетащите комплект файлов на область загрузки или выберете их через диалоговое окно. При необходимости укажите идентификатор сессии загрузки (например, дата, номер запуска и т.д.).
<div class="img" align="center">
<img src="https://github.com/xplainbio/xplainbio-docs/raw/gh-pages/docs/assets/file_manager.png"></img>
</div>

3. Начнется загрузка файлов.
<div class="img" align="center">
<img src="https://github.com/xplainbio/xplainbio-docs/raw/gh-pages/docs/assets/file_upload.png"></img>
</div>

4. Во время загрузки можно перемещаться между окнами менеджера файлов кнопками "Далее" и "Назад", а также вносить изменения в имена образцов, тип мутаций и т.д. Внимательно проверьте правильность привязки файлов к образцам или распределите файлы вручную. Ошибочные образцы можно удалить из списка.
<div class="img" align="center">
<img src="https://github.com/xplainbio/xplainbio-docs/raw/gh-pages/docs/assets/file_upload2.png"></img>
</div>

5. Если все файлы загрузились успешно и правильно привязаны к образцам, становится активна кнопка "Анализировать". Еще раз проверьте правильность настроек и нажмите на нее для запуска анализа образцов.
<div class="img" align="center">
<img src="https://github.com/xplainbio/xplainbio-docs/raw/gh-pages/docs/assets/file_done.png"></img>
</div>