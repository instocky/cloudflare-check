# Туннель для локального сервера

Простой способ открыть доступ к локальному серверу через интернет используя Cloudflared.

## Установка

```bash
winget install --id Cloudflare.cloudflared
```

## Использование

1. Запустите свой локальный сервер
2. В новом терминале выполните:
```bash
cloudflared tunnel --url http://localhost:PORT
```
Замените `PORT` на порт вашего сервера (например, 8080)

## Пример тестового сервера на Python

```python
from http.server import HTTPServer, SimpleHTTPRequestHandler

def run(server_class=HTTPServer, handler_class=SimpleHTTPRequestHandler):
    server_address = ('', 8080)
    httpd = server_class(server_address, handler_class)
    print('Запуск сервера на порту 8080...')
    httpd.serve_forever()

if __name__ == '__main__':
    run()
```

## Ограничения

- Максимум 200 одновременных запросов
- Для тестового использования
- Случайный поддомен при каждом запуске

## Остановка

`Ctrl+C` в терминалах с сервером и туннелем
