# Эрвинделл.
Добро пожаловать в ряды авантюристов. В этом файле написана краткая инструкция о том как начать вести заметки при помощи которых можно трекать состояния золота, опыта и тп.

## TLDR(user):
1. Установить [Obsidian](https://obsidian.md/)
2. Создать новый vault.
3. Зайти в настройки->commutnity plugins и установить "git plugin"
4. Склонить текуший репозиторий
5. Создать папку со своим персонажем в папке "01.Заметки"

## TLDR(lore master):
1. Установить [Obsidian](https://obsidian.md/)
2. Создать новый vault.
3. Зайти в настройки->commutnity plugins и установить "git plugin"
4. Зарегаться на github, форкнуть текуший репозиторий к себе
5. Типичная работа:
  1. Делаешь pull
  2. Редачишь вики (не забываешь указать источник изменений типа "Согласно отчету Х от персонажа У")
  3. Добавляешь изменения к комииту ```git add fileName```
  4. Отправляешь свои изменения на сервер ```git commit -m "описываешь свои изменения в двух словах"; git push origin master```
  5. Создаешь ПР, пишешь об этом в чате хранителей лора.
