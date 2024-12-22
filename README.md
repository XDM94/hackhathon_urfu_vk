# Hackathon URFU + VK

Мы команда 12 - Денис Хламов, Александр Николаев, Нурислам Акбулатов и Павел Очкин - храним здесь свой практикум.

VK Задача 1.
Прямо сейчас здесь находятся наши наработки к чекпоинту.

Как мы распределили роли:
- **Денис Хламов** _тимлид_/_ML-инженер_ - оценивает прогресс, помогает распределять задачи и по доброй (грустной) традиции пишет код руками сам
- **Александр Николаев** - наш _ML-инженер_ - помог настроить пайплайн и построить структуру проекта
- **Нурислам Акбулатов** у нас _аналитик_ - разбирался со структурой и свойствами исходных данных, подсветил подводные камни, помог с препроцессингом
- **Павел Очкин** - _технический писатель_ (ещё немного инженер и аналитик тоже) - помог всё раскомментить и задокументировать, а ещё помогал Нурику в работе с данными

Файлы в репозитории:
- VK_predict.ipynb - ноутбук с выполненным заданием.
- test_users_with_target.csv - предзказания для каждого пользователя из test_users.csv.
- requirements.txt - необходимые библиотеки

## Подготовка данных
### Исходные датасеты:

- **geo_info.csv** — географические данные
- **referer_vectors.csv** — url-адреса где показывается реклама представленные в виде числовых векторов
- **train.csv** — обучающие данные
- **train_labels.csv** — метки для обучающих данных
- **test.csv** — тестовый набор данных
- **test_users.csv** — список пользователей для предсказаний

### Основные этапы обработки данных:
1. Объединение данных из разных источников (`geo_info`, `referer_vectors` и т.д.)
2. Очистка и заполнение пропущенных значений
3. Преобразование признаков:  
    `user_agent` и `request_ts` разбиты на дополнительные колонки которые были закодированы с помощью
    **Label Encoding** и **Ordinal Encoding** для категориальных признаков
5. Удаление нерелевантных и слабокоррелирующих признаков на основе анализа корреляции.

## Обучение модели

Использовалась модель CatBoostClassifier, гиперпараметры которой были оптимизированы с помощью Optuna и проведена оценка важности признаков с помощью SHAP.  
Метрики качества оценивались с помощью:  
- Accuracy - 0.7885885726069863
- Отчета classification_report (precision 0 - 0.80/1 - 0.77, recall 0.79, f1-score 0.79)
- ![image](https://github.com/user-attachments/assets/dae4e1fb-dc5d-494f-8143-9d63b5a70f76)




Результаты предзаказния пола для пользователей из test_users.csv сохранены в `test_users_with_target.csv`  

## Запуск проекта

1. Установите необходимые библиотеки из requirements.txt
2. Запустите ноутбук `VK_predict.ipynb`
3. Убедитесь, что файлы с данными находятся в нужной директории.

Результаты предсказаний сохранятся в `test_users_with_target.csv`.
   
