# python-flask-docker

Домашнее задание
Нужно реализовать rest api на базе flask (пример https://github.com/fimochka-sudo/GB_docker_flask_example)

По шагам: 0. выбрать себе датасет (который интересен или нравится больше всего), сделать pipeline (преобразования + модель), сохранить его на диск. Если не хочется пайплайн, то можно без него, но так вам же будет удобнее потом вызывать его из кода сервиса.

установить удобную для себя среду разработки (pycharm прекрасен - https://www.jetbrains.com/pycharm/)
для вашего проекта вам понадобится requirements.txt с пакетами. Можно за основу взять такой файл из проекта выше. Для его установки прям в pycharm можно открыть терминал и сделать pip install -r requirements.txt (находясь в корне проекта конечно же при этом)
завести себе аккаунт на github (если его еще нет). У самого github есть такой "hello world" по работе с ним - https://guides.github.com/activities/hello-world/
итоговый проект должен содержать: 1) каталог app/models/ (здесь модель-пайплайн предобученная либо код обучения модели-пайплайна) 2) файл app/run_server.py (здесь основной код flask-приложения) 3) requirements.txt (список пакетов, которые у вас используются в проекте - в корне проекта) 4) README.md (здесь какое-то описание, что вы делаете, что за данные, как запускать и т.д) 5) Dockerfile 6) docker-entrypoint.sh
(Опционально): front-end сервис какой-то, который умеет принимать от пользователя введеные данные и ходить в ваш api. На самом деле полезно больше вам, т.к если ваш проект будет далее развиваться (новые модели, интересные подходы), то это хороший пунктик к резюме и в принципе - строчка в портфолио)
Полезные ссылки:

датасеты (для полета мысли): https://www.kaggle.com/datasets
конкурс Сбербанка по недвижимости (можно этот набор данных также взять и обучить модель предсказывать стоимость жилья - неплохой такой сервис может получиться) - https://www.kaggle.com/c/sberbank-russian-housing-market/data Там же и ноутбуки с разными подходами есть.
минималистичный пример связки keras/flask https://blog.keras.io/building-a-simple-keras-deep-learning-rest-api.html для определения класса картинки
неплохой такой пример (помимо того, что разобрали на занятии) связки docker/flask - https://cloud.croc.ru/blog/byt-v-teme/flask-prilozheniya-v-docker/
https://www.digitalocean.com/community/tutorials/how-to-build-and-deploy-a-flask-application-using-docker-on-ubuntu-18-04

Итоговый проект (пример) курса "Машинное обучение в бизнесе"

Данные: с kaggle - https://www.kaggle.com/shivamb/real-or-fake-fake-jobposting-prediction

Задача: предсказать по описанию вакансии является ли она фейком или нет (поле fraudulent). Бинарная классификация

Используемые признаки:

- description (text)
- company_profile (text)
- benefits (text)

Преобразования признаков: tfidf

Модель: logreg

### Клонируем репозиторий и создаем образ
```
$ git clone https://github.com/DirtyBob13/Machine-Learning-in-Business.git
$ cd Machine-Learning-in-Business
$ docker build -t DirtyBob13/Machine-Learning-in-Business .
```

### Запускаем контейнер

Здесь Вам нужно создать каталог локально и сохранить туда предобученную модель (<your_local_path_to_pretrained_models> нужно заменить на полный путь к этому каталогу)
```
$ docker run -d -p 8180:8180 -p 8181:8181 -v <your_local_path_to_pretrained_models>:/DirtyBob/app/models DirtyBob13/Machine-Learning-in-Business

```

### Переходим на localhost:8181
