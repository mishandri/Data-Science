# Данные проекта

Исходные файлы намеренно не лежат в репозитории.

## Откуда брать

Исходник: Brazilian E-Commerce Public Dataset by Olist на Kaggle, лицензия CC BY-NC-SA 4.0.

## Как положить файлы сюда

Самый простой путь: скачать датасет и положить нужные файлы в корень папки проекта,
рядом с ноутбуком. Ноутбуки читают данные относительно своего расположения
(`pd.read_csv('train.csv')`), поэтому после запуска в папке появятся файлы,
которые `.gitignore` не пропустит в репозиторий.

## Скачивание из Kaggle

```python
import kagglehub

path = kagglehub.dataset_download("olistbr/brazilian-ecommerce")
```

Датасет [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce),
лицензия CC BY-NC-SA 4.0. Исходник состоит из нескольких CSV, которые нужно
склеить в плоскую таблицу по `order_id` и подготовить `is_late`. Готовая
плоская версия, соответствующая этому проекту, лежит в папке `data/`
в исходном состоянии задания.
