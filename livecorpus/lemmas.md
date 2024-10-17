Порядок выполнения задания:

1) Импортировал слои words@... для обоих говорящих из ELAN

2) С помощью Notepad оставил в файле только последний столбец со значениями аннотаций (разделенными символом конца строки), используя регулярное выражение:

   Найти: .+\t.+\t.+\t(.+)\n

  Замена: \1\n

3) С помощью mystem разметил столбец токенов, вставил полученный резуьтат в Notepad

4) Перенес знак "=" у прерванных слов (напр. любитель= (любительский) и т.п.) и поставил его до фигурных скобок:

Найти: (.+)(\{.+\})=\n

Замена: \1=\2\n

Далее поставил табуляцию между словами и их леммами в квадратных скобках:

Найти: (.+)(\{.+\})\n

Замена: \1\t\2\n

5) Токены вроде "пошло-поехало", "мультфильм-то", которые mystem распознал как два слова и написал их в одну строку, сделал одним словом. Что делать с двумя грамматическими разметками в двух разных квадратных скобках, не знал, возможно сделал некорректно, тем не менее перевел такие слова в формат "мультфильм-то  {мультфильм=...} ; {то=...}"

Найти: (.+)(\{.+\})(.+)\t(\{.+\})\n

Замена: \1\3\t\2 ; \4\n

6) С помощью excel и ctrl+c ctrl+v совместил выгруженный из ELAN файл с таймкодами и результаты работы в Notepad в одну таблицу

7) Скопировал итоговую таблицу в Notepad

8) С помощью регулярного выражения в последнем столбце оставил только леммы:

Найти: (.+\t.+\t.+\t)\{(.+?)=.+\}\n

Замена: \1\2\n

Также заменил words@... на lemma@... простой заменой

9) Скопировал итоговую таблицу из Excel в файл Notepad во второй раз в последнюю строку после всех lemma@...

10) С помощью регулярных выражений в последнем столбце оставил только морфологическую разметку:

Найти: (.+\t.+\t.+\t)\{.+?=(.+)\}\n

Замена: \1\2\n

Для слов, у которых mystem не смог определить грамматику и написал "??", использовал выражение:

Найти: (.+\t.+\t.+\t)\{.+\?\?\}\n

Замена: \1\?\?\n

Также заменил words@... на morph@... простой заменой

11) Импортировал полученный текстовый файл в ELAN, указав табуляцию в качестве разделителя