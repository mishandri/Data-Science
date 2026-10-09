Решенные задачи по машинному обучению на реальных бизнес-данных: регрессия и классификация на таблицах, learning to rank, поиск изображений по embeddings, ассоциативные правила и кластеризация.

Девять проектов, в каждом папке ноутбук с решением, readme с разбором и `result.csv` с предсказаниями. Данные не лежат в репозитории, см. `data/README.md` внутри проекта.

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
| [Поиск товаров по визуальному сходству](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D0%B8%20%D0%B4%D0%BB%D1%8F%20%D0%BF%D0%BE%D0%B8%D1%81%D0%BA%D0%B0%20%D1%82%D0%BE%D0%B2%D0%B0%D1%80%D0%BE%D0%B2%20%D0%BF%D0%BE%20%D0%B8%D1%85%20%D0%B2%D0%B8%D0%B7%D1%83%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%BC%D1%83%20%D1%81%D1%85%D0%BE%D0%B4%D1%81%D1%82%D0%B2%D1%83%20(CNN)) | поиск по изображению | VGG16 без классификационного слоя, косинусный поиск | Accuracy = 0.72 (порог 0.7) |
| [Товарные рекомендации на основе ассоциативных правил](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D1%82%D0%BE%D0%B2%D0%B0%D1%80%D0%BD%D1%8B%D1%85%20%D1%80%D0%B5%D0%BA%D0%BE%D0%BC%D0%B5%D0%BD%D0%B4%D0%B0%D1%86%D0%B8%D0%B9%20%D0%BD%D0%B0%20%D0%BE%D1%81%D0%BD%D0%BE%D0%B2%D0%B5%20%D0%B0%D1%81%D1%81%D0%BE%D1%86%D0%B8%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D1%8B%D1%85%20%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB) | правила ассоциации | Apriori, support 0.05, confidence 0.5 | Accuracy = 0.909 (порог 0.6) |
| [Кластеризация базы клиентов](https://github.com/mishandri/Data-Science/tree/main/%D0%A0%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%BA%D0%B0%20%D0%BC%D0%BE%D0%B5%D0%B4%D0%BB%D0%B8%20%D0%BA%D0%BB%D0%B0%D1%81%D1%82%D0%B5%D1%80%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8%20%D0%B1%D0%B0%D0%B7%D1%8B%20%D0%BA%D0%BB%D0%B8%D0%B5%D0%BD%D1%82%D0%BE%D0%B2) | кластеризация с эталонами | KMeans с центрами из `exemplar.csv`, PCA для визуализации | Accuracy = 0.802 (порог 0.8) |
| [Анализ клиентов кредитных карт](https://github.com/mishandri/Data-Science/tree/main/%D0%90%D0%BD%D0%B0%D0%BB%D0%B8%D0%B7%20%D0%BA%D0%BB%D0%B8%D0%B5%D0%BD%D1%82%D0%BE%D0%B2%20%D0%BA%D1%80%D0%B5%D0%B4%D0%B8%D1%82%D0%BD%D1%8B%D1%85%20%D0%BA%D0%B0%D1%80%D1%82%20%D1%81%20%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%20%D0%BC%D0%B5%D1%82%D0%BE%D0%B4%D0%BE%D0%B2%20%D0%BA%D0%BB%D0%B0%D1%81%D1%82%D0%B5%D1%80%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8) | кластеризация + аномалии | DBSCAN, перебор 528 комбинаций `eps` и `min_samples` | Silhouette = 0.341, CH = 71.6 |

## Стек

Python 3.11, pandas, numpy, scikit-learn, XGBoost, PyTorch, torchvision, mlxtend, matplotlib, seaborn, plotly. В каждом проекте свой `requirements.txt`.

## English

Machine learning projects built on real business data: tabular regression and classification, learning to rank, image retrieval with CNN embeddings, association rules and clustering. Each project has its own notebook, a write-up in Russian and a `result.csv` with predictions. Datasets are not stored in the repo, see `data/README.md` inside each project.