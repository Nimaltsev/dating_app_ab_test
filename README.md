# Dating app A/B test
### Анализ данных A/B-теста приложения для онлайн-знакомств

**Контекст и задача**  
В данном проекте рассматриваются данные приложения для онлайн-знакомств.  
Механика приложения следующая: пользователи видят в приложении анкеты друг друга и могут ставить друг другу лайки или дизлайки. Если пользователи поставили друг другу лайк – это называется мэтч, и у пользователей появляется возможность познакомиться.  
Командой приложения разработан новый алгоритм для поиска наиболее подходящих анкет. Мной проведен анализ результатов A/B-теста, проведенного для новой механики. В рамках теста все пользователи были разделены на две группы. Пользователи в группе с номером 0 пользовались приложением со старым алгоритмом. Все пользователи в группе 1 пользовались приложением с новым алгоритмом для поиска анкет.  
Задача – оценить, смогла ли новая механика приносить больше удовлетворения пользователям.  
В данных находятся разделенные на группы (тест и контроль) данные о лайках и мэтчах пользователей.

**Используемый стек**<br>
Python, pandas, seaborn, numpy, statsmodels, scipy stats.

**Этапы работы:** <br> 
1. В качестве исходных данных представлена 1 таблица (с заказами, юзерами и данными о товарах). Первым шагом проведён предварительный анализ данных на предмет пропусков, дублей и т.д.
2. В качестве первой метрики выбрано оценить _среднее количество мэтчей на пользователя_. Нулевая гипотеза: новая механика не влияет на выбранную метрику.
3. Я предварительно оценил величины выбранной метрики для каждой из групп, не используя стат.критерий, а также взглянул на метрику на графиках. Если взглянуть на распределения по группам, то видно, что группа 1 (с новой механикой) имеет более высокое среднее количество мэтчей (8-9) и нормальное распределение. В группе со старой механикой большая часть пользователей имеют 1-2 мэтча, распределение близко к экспоненциальноиу.
4. Методом линейной регресси я сравнил 2 категориальные переменные. Согласно полученным данным с применением новой механики есть статистически значимое увеличение количества мэтчей на пользователя
5. Дополнительно сравнены значения методом bootstrap, получены статистически значимые различия (доверительные интервалы не пересекаются) 
6. В качестве еще одной метрики я выяснил, выросло ли _общее количество активностей_ на пользователя.
7. Распределения метрики в обеих выборках близки к нормальным, нет значительных выбросов. Так как выборки довольно большие, допустимо провести t-тест (предварительно проверил гомогенность дисперсий критерием Левена). По результатам теста также есть статистически значимый рост целевой метрики ( _общее количество активностей_ на пользователя)
8. Сформулирован вывод  
  
**Результат**<br>
Вывод: рост среднего количества мэтчей на юзера статистически значим, следовательно качество сервиса выросло, целесообразно выкатить изменения на всю аудиторию. Кроме того, выросло и общее количество взаимодействий, что явно показало более высокую вовлеченность пользователей


По результатам проведенного анализа вынесена рекомендация раскатить новую систему рекомендаций на всех пользователей
