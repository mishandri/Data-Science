Учебные задачи по машинному обучению: регрессия и классификация на таблицах, learning to rank, поиск изображений по эмбеддингам, ассоциативные правила и кластеризация.

Девять задач с курса-симулятора. Формат везде одинаковый: готовые `train.csv` и `test.csv`, в ТЗ указан минимальный порог метрики, на выходе CSV с предсказаниями. Это учебные задания, а не рабочие проекты, поэтому ниже описываю не постановку, а то, что сделано сверх неё.

В каждой папке: ноутбук с решением, readme с разбором, `result.csv` с предсказаниями и `requirements.txt`. Данные не лежат в репозитории, см. `data/README.md` внутри проекта.

## Что сделано сверх постановки

Курсовые задачи обычно решаются минимальным способом: обучил, отдал файл. Я попробовал доводить их до конца, и это главное, что здесь есть.

* **Валидация на отложенной выборке** в четырёх supervised-проектах. В исходных ноутбуках её не было нигде, метрики просто приходили с платформы.
* **Разбор ошибок.** В ресторане accuracy 0.82, но macro F1 0.58: класс `Low` не распознан ни разу. В задержках precision на опозданиях 0.27, то есть больше половины прогнозов «опоздал» ошибочны.
* **Проверка, что задача выполнена.** В кластеризации кредитных карт требовалось 4 кластера, DBSCAN дал 5, а метрики считались с утечкой метки в признаки.
* **Важность признаков**, из которой видно, что задержки определяет сезонность, а не цена товара или скорость обработки заказа.
* **Интерпретация сегментов:** в кластеризации McDonald's сегменты разделяет частота визитов, а не отношение к бренду.
* **Честный разбор слабых мест.** В каждом readme есть раздел с ограничениями, включая те, которые нашёл сам.

## Проекты с учителем

| Проект | Задача | Решение | Метрика (порог из ТЗ) |
|---|---|---|---|
| [Предсказание стоимости недвижимости](https://github.com/mishandri/Data-Science/tree/main/%D0%9F%D1%80%D0%B5%D0%B4%D1%81%D0%BA%D0%B0%D0%B7%D0%B0%D0%BD%D0%B8%D0%B5%20%D1%81%D1%82%D0%BE%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D0%B8%20%D0%BD%D0%B5%D0%B4%D0%B2%D0%B8%D0%B6%D0%B8%D0%BC%D0%BE%D1%81%D1%82%D0%B8) | регрессия | полиномиальные признаки 3 степени + Lasso | R² = 0.686 (0.6) |
| [Предсказание задержек транспортной компании](https://github.com/mishandri/Data-Science/tree/main/%D0%9F%D1%80%D0%B5%D0%B4%D1%81%D0%BA%D0%B0%D0%B7%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%B7%D0%B0%D0%B4%D0%B5%D1%80%D0%B6%D0%B5%D0%BA%20%D1%82%D1%80%D0%B0%D0%BD%D1%81%D0%BF%D0%BE%D1%80%D1%82%D0%BD%D0%BE%D0%B9%20%D0%BA%D0%BE%D0%BC%D0%BF%D0%B0%D0%BD%D0%B8%D0%B8) | бинарная классификация | Random Forest на 10 производных признаках, frequency encoding | F1 = 0.326 (0.3) |
| [Рекомендательная система для интернет-магазина](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F%20%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B0%20%D0%B4%D0%BB%D1%8F%20%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82-%D0%BC%D0%B0%D0%B3%D0%B0%D0%B7%D0%B8%D0%BD%D0%B0) | learning to rank | XGBoost `rank:ndcg`, split по пользователям, early stopping | NDCG@5 = 0.946 (0.9) |
| [Прогнозирование рентабельности ресторана](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B5%D0%BD%D1%82%D0%B0%D0%B1%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE%D1%81%D1%82%D1%8C%20%D1%80%D0%B5%D1%81%D1%82%D0%BE%D1%80%D0%B0%D0%BD%D0%B0) | 3-классовая классификация | One-vs-Rest LogisticRegression, разбор `Ingredients` в бинарные признаки | Accuracy = 0.815 (0.75) |
| [Таргетированный маркетинг](https://github.com/mishandri/Data-Science/tree/main/%D0%A2%D0%B0%D1%80%D0%B3%D0%B5%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D1%8B%D0%B9%20%D0%BC%D0%B0%D1%80%D0%BA%D0%B5%D1%82%D0%B8%D0%BD%D0%B3) | бинарная классификация | GaussianNB, порядковое кодирование, MinMax | метрика в ТЗ не задана |

## Проекты без учителя и поиск по эмбеддингам

| Проект | Задача | Решение | Метрика |
|---|---|---|---|
| [Поиск товаров по визуальному сходству](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D0%B8%20%D0%B4%D0%BB%D1%8F%20%D0%BF%D0%BE%D0%B8%D1%81%D0%BA%D0%B0%20%D1%82%D0%BE%D0%B2%D0%B0%D1%80%D0%BE%D0%B2%20%D0%BF%D0%BE%20%D0%B8%D1%85%20%D0%B2%D0%B8%D0%B7%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%BC%D1%83%20%D1%81%D1%85%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D1%83%20%28CNN%29) | поиск по изображению | VGG16 без классификационного слоя, косинусный поиск | Accuracy = 0.72 (порог 0.7) |
| [Товарные рекомендации на основе ассоциативных правил](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D1%82%D0%BE%D0%B2%D0%B0%D1%80%D0%BD%D1%8B%D1%85%20%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D0%B0%D1%86%D0%B8%D0%B9%20%D0%BD%D0%B0%20%D0%BE%D1%81%D0%BD%D0%BE%D0%B2%D0%B5%20%D0%B0%D1%81%D1%81%D0%BE%D1%86%D0%B8%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D1%8B%D1%85%20%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB) | правила ассоциации | Apriori, support 0.05, confidence 0.5 | Accuracy = 0.909 (порог 0.6) |
| [Кластеризация базы клиентов](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D0%BC%D0%BE%D0%B5%D0%B4%D0%BB%D0%B8%20%D0%BA%D0%BB%D0%B0%D1%81%D1%82%D0%B5%D1%80%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8%20%D0%B1%D0%B0%D0%B7%D1%8B%20%D0%BA%D0%BB%D0%B8%D0%B5%D0%BD%D1%82%D0%BE%D0%B2) | кластеризация с эталонами | KMeans с центрами из `exemplar.csv`, PCA для визуализации | Accuracy = 0.802 (порог 0.8) |
| [Анализ клиентов кредитных карт](https://github.com/mishandri/Data-Science/tree/main/%D0%90%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7%20%D0%BA%D0%BB%D0%B8%D0%B5%D0%BD%D1%82%D0%BE%D0%B2%20%D0%BA%D1%80%D0%B5%D0%B4%D0%B8%D1%82%D0%BD%D1%8B%D1%85%20%D0%BA%D0%B0%D1%80%D1%82%20%D1%81%20%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%D0%BC%20%D0%BC%D0%B5%D1%82%D0%BE%D0%B4%D0%BE%D0%B2%20%D0%BA%D0%BB%D0%B0%D1%81%D1%82%D0%B5%D1%80%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8) | кластеризация + аномалии | DBSCAN, перебор 528 комбинаций `eps` и `min_samples` | **задача не выполнена**, подробности в readme |

## Что ещё предстоит доделать

Честный список того, что я знаю про эти проекты, но пока не исправил. Подробности и обоснования в readme каждого проекта.

* В недвижимости и таргетинге масштабирование обучается отдельно на train и test, то есть границы подстраиваются под тестовую выборку.
* В ресторане не хватает `class_weight`, из-за чего редкий класс не распознаётся.
* В рекомендательной системе `dtrain` строится по всей выборке, и early stopping видит валидацию. Проверил: метрика завышена примерно на 0.006.
* В CNN аугментации применяются к каталогу при инференции, поэтому результат не воспроизводится от запуска к запуску.
* В кредитных картах DBSCAN не подходит под требование «ровно 4 кластера», нужна замена на KMeans.

## Стек

Python 3.11, pandas, numpy, scikit-learn, XGBoost, PyTorch, torchvision, mlxtend, matplotlib, seaborn, plotly. В каждом проекте свой `requirements.txt`.

## English

Study ML tasks: tabular regression and classification, learning to rank, image retrieval with CNN embeddings, association rules and clustering. These come from a course simulator, not from production work, so each readme describes what was done on top of the assignment rather than the assignment itself. On top: holdout validation, error analysis, feature importance, segment interpretation and an honest list of limitations. Each project has its own notebook, a write-up in Russian, a `result.csv` with predictions and a `requirements.txt`. Datasets are not stored in the repo, see `data/README.md` inside each project.
