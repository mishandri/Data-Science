# Данные проекта

Файлы соревнования намеренно не лежат в репозитории: вместе с распакованным пакетом
`jpx_tokyo_market_prediction` они занимают больше 1 ГБ. Здесь только то, что нужно,
чтобы их получить и положить куда надо.

## Откуда брать

Всё это — [данные соревнования JPX Tokyo Stock Exchange Prediction](https://www.kaggle.com/competitions/jpx-tokyo-stock-exchange-prediction/data).
Публичных зеркал с тем же набором файлов нет, скачивание доступно только зарегистрированным
участникам Kaggle.

Соревнование закрыто, но файлы на странице Data лежат: отправлять решения нельзя, а
скачать данные для воспроизведения — можно.

Что нужно в итоге:

```
train_files/            # основная история, 2017-01-04 — 2021-12-03
supplemental_files/     # добавка до 2022-06-24, без неё обучение короче на 135 дней
example_test_files/     # нужны для локальной имитации API: local_submission.csv
data_specifications/    # описания колонок, для ноутбука не обязательны
stock_list.csv          # справочник бумаг, в ноутбуке не используется
jpx_tokyo_market_prediction/   # сам time-series API, только для запуска на Kaggle
```

## Как скачать

Нужен аккаунт Kaggle и токен из **Settings → API → Create New Token**.

1. `pip install kaggle`
2. положить скачанный `kaggle.json` в `C:\Users\<user>\.kaggle\` (Windows)
   или `~/.kaggle/` (Linux, macOS);
3. скачать:

   ```bash
   kaggle competitions download -c jpx-tokyo-stock-exchange-prediction -p <путь>
   ```

4. распаковать архив.

`kaggle.json` — это секрет, коммитить его нельзя. Файл уже покрыт `.gitignore`
на уровне репозитория, но и в общий доступ он выкладываться не должен.

Если нет возможности ставить `kaggle` локально, есть путь через сам Kaggle: **Add data →
Competition data → jpx-tokyo-stock-exchange-prediction** в интерфейсе ноутбука. Тогда
файлы появятся в `/kaggle/input/...`, и ноутбук найдёт их сам.

## Как положить файлы

Распакованные папки кладутся **рядом с ноутбуком**, то есть в корень папки проекта
`Kaggle-соревнование JPX Tokyo Stock Exchange Prediction`:

```
Kaggle-соревнование JPX Tokyo Stock Exchange Prediction/
├── jpx_tokyo_market_prediction.ipynb
├── train_files/stock_prices.csv
├── supplemental_files/stock_prices.csv
├── example_test_files/…
├── data/README.md
└── …
```

Ноутбук ищет корень с данными функцией `find_data_dir()`: пробует `.`, `..` и `../..`,
а на Kaggle рекурсивно обходит `/kaggle/input`. Поэтому допустимы только эти три уровня,
и **положить данные в эту папку `data/` нельзя** — ноутбук её не увидит и упадёт с
`FileNotFoundError: Не найден каталог с train_files/stock_prices.csv`.

Достаточно `train_files/` для обучения. `supplemental_files/` добавляет последние 135
дней и заметно поднимает качество — без неё валидация заканчивается в декабре 2021.
`example_test_files/` нужен только для локального прогона: без него ноутбук отработает
всё до последней ячейки и не сможет записать `local_submission.csv`.

Пакет `jpx_tokyo_market_prediction` локально бесполезен — он скомпилирован под CPython 3.7
и на обычной машине не импортируется. Локально включается имитация `local_iter_test()`.