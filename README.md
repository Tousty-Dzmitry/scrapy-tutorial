# Проект scrapy-tutorial

Этот проект представляет собой веб-скрейпер на основе Scrapy, предназначенный для извлечения данных с веб-сайтов. Пример реализации демонстрирует парсинг цитат с сайта [quotes.toscrape.com](http://quotes.toscrape.com).

## Оглавление

- [Обзор проекта](#обзор-проекта)
- [Установка](#установка)
- [Использование](#использование)
- [Структура проекта](#структура-проекта)
- [Ключевые особенности](#ключевые-особенности)
- [Настройка](#настройка)
- [Лицензия](#лицензия)

## Обзор проекта

Этот проект Scrapy включает базового паука (`QuotesSpider`), который собирает цитаты с нескольких страниц сайта [quotes.toscrape.com](http://quotes.toscrape.com). Собираемые данные включают:

- Текст цитаты

## Установка

Выполните следующие шаги для настройки проекта:

1. Клонируйте репозиторий:
   ```bash
   git clone git@github.com:Tousty-Dzmitry/scrapy-tutorial.git
   cd scrapy-tutorial
   ```

2. Создайте и активируйте виртуальное окружение (опционально, но рекомендуется):
   ```bash
   python -m venv venv
   source venv/bin/activate  # Для Windows: venv\Scripts\activate
   ```

3. Установите необходимые зависимости:
   ```bash
   pip install scrapy
   ```

## Использование

### Запуск паука

Для запуска `QuotesSpider` выполните следующую команду:

```bash
scrapy crawl quotes
```

### Сохранение результатов

Вы можете сохранить собранные данные в файл в различных форматах, таких как JSON или CSV:

- JSON:
  ```bash
  scrapy crawl quotes -o quotes.json
  ```

- CSV:
  ```bash
  scrapy crawl quotes -o quotes.csv
  ```

## Структура проекта

```
scrapy-python/
├── scrapy.cfg                 # Конфигурационный файл Scrapy
├── scrapy-tutorial/             # Основной пакет проекта
│   ├── __init__.py
│   ├── items.py               # Определение моделей элементов
│   ├── middlewares.py         # Пользовательские middlewares
│   ├── pipelines.py           # Обработка данных
│   ├── settings.py            # Настройки проекта
│   └── spiders/               # Определение пауков
│       ├── __init__.py
│       └── quotes_spider.py   # Пример паука
```

## Ключевые особенности

- **Middleware паука**: Пользовательские middlewares, определенные в `middlewares.py`, для обработки запросов и ответов.
- **Middleware загрузчика**: Пользовательские middleware загрузчика для модификации HTTP-запросов.
- **Конвейеры обработки данных**: Обрабатывают собранные данные перед их сохранением.
- **Настройки**: Настраиваемые параметры, такие как `DOWNLOAD_DELAY` и `ITEM_PIPELINES`.

## Настройка

### Изменение паука

Чтобы адаптировать паука для других веб-сайтов, измените `start_urls` и логику парсинга в `quotes_spider.py`.

### Настройка параметров

Ключевые параметры в `settings.py`:

- **Задержка загрузки**:
  ```python
  DOWNLOAD_DELAY = 3  # Регулировка задержки между запросами
  ```
- **Конвейеры обработки данных**:
  ```python
  ITEM_PIPELINES = {
      "scrapy-tutorial.pipelines.ScrapyPythonPipeline": 300,
  }
  ```
