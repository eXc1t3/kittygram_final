## Описание проекта

Соцсеть с возможностью публикации фотографий ваших любимых котиков 😻

## Стек

- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- JavaScript
- Nginx
- Docker compose

## Запуск проекта из образов с Docker hub

Cоздаём папку проекта `kittygram` и переходим в нее:

```bash
mkdir kittygram
cd kittygram
```

В папку проекта копируем (или создаём) файл `docker-compose.production.yml` и запускаем его:

```bash
sudo docker compose -f docker-compose.production.yml up
```

Далее происходит скачивание образов, создание и включение контейнеров, создание томов и сети.


## Запуск проекта из исходников GitHub

Клонируем себе репозиторий: 

```bash 
git clone https://github.com/eXc1t3/kittygram_final
```

Выполняем запуск:

```bash
sudo docker compose -f docker-compose.yml up
```

## После запуска: -миграции; -сбор статистики

После запуска нужно выполнить сбор статистики и миграцию для бэкенда. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py migrate

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py collectstatic

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend cp -r /app/collected_static/. /static/static/
```

теперь проект доступен на: 

```
http://localhost:9000/
```

## Описание переменных окружения .env

Ниже пример файла .env c переменными окружения, необходимыми для запуска приложения:

```bash
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
DB_HOST=db
DEBUG=False
SECRET_KEY=django_secret_key_example
```


## Остановка оркестра контейнеров

В том же окне терминала, где был запуск: **Ctrl+С** или в другом окне:

```bash
sudo docker compose -f docker-compose.yml down
```

## Автор
Орлан Узум https://github.com/eXc1t3
