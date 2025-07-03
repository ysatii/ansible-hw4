# Ansible Роль: lighthouse-role

Эта роль устанавливает и настраивает [Lighthouse](https://github.com/VKCOM/lighthouse) — веб-интерфейс для визуализации запросов к ClickHouse.

##  Возможности

- Устанавливает Nginx и необходимые пакеты
- Загружает Lighthouse с GitHub
- Распаковывает и размещает файлы в каталоге Nginx
- Создаёт конфигурацию Nginx для доступа к Lighthouse
- Запускает и включает службу `nginx`

##  Пример использования

```yaml
- hosts: web
  become: true
  roles:
    - role: lighthouse-role
```

##  Конфигурация

Nginx настраивается на:

- Прослушивание порта `80`
- Обслуживание содержимого из `/usr/share/nginx/html/lighthouse-master/`
- Поддержку SPA (одностраничного приложения) через fallback на `index.html`

Дополнительные переменные не требуются — все пути и параметры заданы по умолчанию.

##  Требования

- ОС на базе RHEL/CentOS с `yum` и доступом к `epel-release`
- root-доступ или `become: true`

##  Лицензия

MIT
