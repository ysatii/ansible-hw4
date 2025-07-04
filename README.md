# Домашнее задание к занятию 4 «Работа с roles» - Мельник Юрий Александрович

## Подготовка к выполнению

1. * Необязательно. Познакомьтесь с [LightHouse](https://youtu.be/ymlrNlaHzIY?t=929).
2. Создайте два пустых публичных репозитория в любом своём проекте: vector-role и lighthouse-role.
3. Добавьте публичную часть своего ключа к своему профилю на GitHub.

## Основная часть

Ваша цель — разбить ваш playbook на отдельные roles. 

Задача — сделать roles для ClickHouse, Vector и LightHouse и написать playbook для использования этих ролей. 

Ожидаемый результат — существуют три ваших репозитория: два с roles и один с playbook.

**Что нужно сделать**

1. Создайте в старой версии playbook файл `requirements.yml` и заполните его содержимым:

   ```yaml
   ---
     - src: git@github.com:AlexeySetevoi/ansible-clickhouse.git
       scm: git
       version: "1.13"
       name: clickhouse 
   ```

2. При помощи `ansible-galaxy` скачайте себе эту роль.
3. Создайте новый каталог с ролью при помощи `ansible-galaxy role init vector-role`.
4. На основе tasks из старого playbook заполните новую role. Разнесите переменные между `vars` и `default`. 
5. Перенести нужные шаблоны конфигов в `templates`.
6. Опишите в `README.md` обе роли и их параметры. Пример качественной документации ansible role [по ссылке](https://github.com/cloudalchemy/ansible-prometheus).
7. Повторите шаги 3–6 для LightHouse. Помните, что одна роль должна настраивать один продукт.
8. Выложите все roles в репозитории. Проставьте теги, используя семантическую нумерацию. Добавьте roles в `requirements.yml` в playbook.
9. Переработайте playbook на использование roles. Не забудьте про зависимости LightHouse и возможности совмещения `roles` с `tasks`.
10. Выложите playbook в репозиторий.
11. В ответе дайте ссылки на оба репозитория с roles и одну ссылку на репозиторий с playbook.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---

## Решение
скачиваем роль   
```
ansible-galaxy install -r requirements.yml -p ./roles  
mv roles/clickhouse roles/clickhouse-role  
```

инициализируем пустые роли
```
ansible-galaxy role init roles/vector-role
ansible-galaxy role init roles/lighthouse-role
```

из папки  ansible-hw4/ansible-hw4/playbook/

командой
```
ansible-playbook -i inventory/prod.yml site.yml
```

Начнеться выплнение пайл-план!

![рисунок 1](https://github.com/ysatii/ansible-hw4/blob/main/img/img_1.jpg)
![рисунок 2](https://github.com/ysatii/ansible-hw4/blob/main/img/img_2.jpg)

смотрим данные по адресу http://84.201.180.24/?user=default#http://84.201.171.156:8123 его даст сам пай-плайн  
![рисунок 3](https://github.com/ysatii/ansible-hw4/blob/main/img/img_3.jpg)
данные продолжают поступапать при обновлениии страниицы 
![рисунок 4](https://github.com/ysatii/ansible-hw4/blob/main/img/img_4.jpg)

Будут установлены clickhouse, lighthouse, vector 
клинет vector будет установлен на две машины  
- **lighthouse** - получаем данные о запросах к nginx, 
-  **vector** - получаем данные о работе сервера **vector**  
на машину вектор будет установлен сервер **vector**

создадим **vector-role** в гит репозитории и протегеруем! переместим туда файлы и описание роли
![рисунок 5](https://github.com/ysatii/ansible-hw4/blob/main/img/img_5.jpg)
роль доступна  по адресу  https://github.com/ysatii/vector-role

создадим роль **lighthouse-role** в гит репозитории и протегеруем! переместим туда файлы и описание роли
![рисунок 5](https://github.com/ysatii/ansible-hw4/blob/main/img/img_5.jpg)
роль доступна  по адресу  https://github.com/ysatii/lighthouse-role

репозиторий с рабочим плайбук  https://github.com/ysatii/ansible-hw4/tree/main/playbook 






