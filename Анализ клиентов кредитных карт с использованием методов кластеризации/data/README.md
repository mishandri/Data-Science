# Данные проекта

Исходные файлы намеренно не лежат в репозитории.

## Откуда брать

Датасет CC GENERAL с Kaggle, лицензия CC0 (public domain).

## Как положить файлы сюда

Самый простой путь: скачать датасет и положить нужные файлы в корень папки проекта,
рядом с ноутбуком. Ноутбуки читают данные относительно своего расположения
(`pd.read_csv('train.csv')`), поэтому после запуска в папке появятся файлы,
которые `.gitignore` не пропустит в репозиторий.

## Скачивание из Kaggle

```python
import kagglehub

path = kagglehub.dataset_download("arjunbhasin2013/ccdata")
df = pd.read_csv(path + "/CC_GENERAL.csv", index_col="CUST_ID")
```

Датасет [Credit Card Dataset for Clustering](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata),
лицензия CC0, около 100 тысяч загрузок.
