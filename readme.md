## Подготовка окружения к мастер-классу

Выполните все шаги заранее.

---

# 1. Установить необходимые программы

## **Node.js (LTS)**

Скачать:
[https://nodejs.org](https://nodejs.org)

После установки выполнить:

```bash
node -v
npm -v
```

**Что вы должны увидеть:**

* Команда выводит номер версии.
* Ошибок быть не должно.

Пример (актуальная LTS на сегодня):

```
node -v
v20.18.0

npm -v
10.8.2
```

---

## **Git**

Скачать:
[https://git-scm.com](https://git-scm.com)

Проверить установку:

```bash
git --version
```

Должна показаться версия, например:

```
git version 2.45.1
```

---

## **Docker Desktop**

Скачать:
[https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

### Как убедиться, что Docker запущен

1. Значок Docker должен быть виден в системном трее (Windows) или верхней панели (macOS).
2. Выполнить в терминале:

   ```bash
   docker --version
   ```

   Должна появиться версия Docker, например:

   ```
   Docker version 27.1.2, build cb74dfc
   ```

Ошибок быть не должно.

---

# 2. Подготовить локальную базу данных

Создать любую папку, например:

```
squid-masterclass
```

Внутри создать файл **docker-compose.yml**:

```yaml
services:
  postgres:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: squid_admin
      POSTGRES_PASSWORD: squid_pass
      POSTGRES_DB: squid_game
    ports:
      - "5432:5432"

  adminer:
    image: adminer
    ports:
      - "8080:8080"
    environment:
      ADMINER_DEFAULT_SERVER: postgres
```

Запуск контейнеров:

```bash
docker compose up -d
```

Если Docker работает — локальная база и веб-интерфейс развернутся автоматически.

---

# 3. Как открыть Adminer

**Adminer (веб-интерфейс для БД)**
Открыть в браузере:
[http://localhost:8080](http://localhost:8080)

Данные для входа:

* **System:** PostgreSQL
* **Server:** postgres
* **User:** squid_admin
* **Password:** squid_pass
* **Database:** squid_game

---

# 4. Готово

Если всё установлено и `docker compose up -d` работает без ошибок — вы готовы к мастер-классу.
