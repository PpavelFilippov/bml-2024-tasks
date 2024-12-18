### [Regression with an Abalone Dataset](https://www.kaggle.com/competitions/playground-series-s4e4/overview). 

__Цель__ - предсказать возраст моллюска на основе различных физических измерений.

__Модель:__ AdaBoost

__Должно быть выполнено:__
1) Исследовательский анализ данных (EDA)
2) Предварительная обработка данных
3) Построение и оценка модели

    # Теоретическая информация о AdaBoost


AdaBoost (Adaptive Boosting) — это алгоритм машинного обучения, использующий ансамблевый подход для построения сильного классификатора или регрессора из множества слабых. 
Слабый классификатор — это модель, которая немного лучше случайного угадывания.  AdaBoost последовательно обучает слабые классификаторы, 
придавая больший вес образцам, которые были неправильно классифицированы предыдущими классификаторами. 

Алгоритм AdaBoost работает следующим образом:

1. **Инициализация весов:** Назначается равный вес каждому образцу в обучающем наборе.
2. **Итеративное обучение:** На каждой итерации:
    * Обучается слабый классификатор на взвешенном обучающем наборе.
    * Вычисляется ошибка классификатора.
    * Определяется вес классификатора, который обратно пропорционален его ошибке.
    * Веса образцов обновляются: образцы, неправильно классифицированные, получают больший вес, а правильно классифицированные — меньший.
3. **Объединение классификаторов:**  Полученные слабые классификаторы объединяются взвешенным голосованием, где вес каждого классификатора пропорционален его точности.  
   В случае регрессии, предсказания усредняются с весами.

**Преимущества AdaBoost:**

• Простота реализации и высокая эффективность.
• Способность обрабатывать данные с высоким уровнем шума и выбросов.
• Не требует сложной настройки гиперпараметров.

**Недостатки AdaBoost:**

• Чувствителен к выбросам в данных.
• Может переобучиться, если количество итераций слишком велико.

![image_2024-12-04_16-05-03](https://github.com/user-attachments/assets/e6d4dbdd-2c4d-426f-b5cf-490d9979d3b4)
![image_2024-12-04_16-05-33](https://github.com/user-attachments/assets/d45c439c-c792-4c63-a06c-42049219056e)
![image_2024-12-04_16-05-17](https://github.com/user-attachments/assets/71bcb420-9947-4d03-80bf-fee0ac0765d1)


# Модель предсказания возраста моллюсков

Этот репозиторий содержит код Python для предсказания возраста моллюска (количество колец) на основе различных физических измерений, используя модель AdaBoostRegressor.

## Описание

Код выполняет следующие шаги:

1. Загрузка данных:  Загружает данные из файла data.txt, расположенного в той же директории, что и скрипт.  Ожидается, что данные разделены запятыми.
2. Предварительная обработка данных:  Обрабатывает дубликаты столбцов, разделяет данные на обучающую и тестовую выборки, кодирует категориальный признак 'Sex' и масштабирует числовые признаки с помощью StandardScaler.
3. EDA (Исследовательский анализ данных):  Выполняет визуализацию данных с помощью matplotlib и seaborn, включая гистограммы, boxplots и подсчет количества наблюдений для категориальных переменных. Проводит тест Kruskal-Wallis для проверки значимости влияния каждого признака на количество колец.
4. Обучение модели:  Обучает модель AdaBoostRegressor на масштабированных обучающих данных.
5. Оценка модели:  Вычисляет среднеквадратичную ошибку (MSE) на валидационной выборке.
6. Предсказание:  Делает предсказания возраста моллюсков на тестовой выборке.
7. Сохранение результатов:  Сохраняет предсказания в файл submission.csv.

## Требования

•   Python 3.x
•   Библиотеки: pandas, numpy, matplotlib, seaborn, scipy, scikit-learn

Установите необходимые библиотеки с помощью:

pip install pandas numpy matplotlib seaborn scipy scikit-learn


## Использование

1.  Создайте файл data.txt с данными в формате CSV (разделитель - запятая).  Пример структуры данных:

    ```
    id,Sex,Length,Diameter,Height,Whole weight,Shell weight,Rings
    0,M,0.455,0.365,0.095,0.5140,0.2245,7
    1,M,0.350,0.265,0.090,0.2255,0.0995,7
    ...
    ```

2.  Запустите скрипт Python.  Результат (предсказания) будет сохранен в файл submission.csv.


##  Примечания

•   Файл data.txt должен находиться в той же директории, что и скрипт Python.
•   Код содержит EDA-часть, которая генерирует графики.  Эти графики выводятся на экран.
•   В предобработке данных используется факторизация категориального признака Sex.
•   Модель AdaBoostRegressor выбрана для предсказания регрессии (непрерывной переменной).
•   В качестве метрики качества используется MSE.

*Фирсова Варвара*
