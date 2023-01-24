# python-flask-docker
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
