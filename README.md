# insta-api

API REST de una red social tipo Instagram. La hice para el proyecto de aula de la universidad, y la usa la app móvil [instaIonic](https://github.com/santi382/instaIonic).

Está hecha con Laravel 12 y PHP 8.2. La autenticación es por tokens con Laravel Sanctum.

## Qué hace

- Registro, inicio y cierre de sesión
- Publicaciones: listar, crear, ver y borrar
- Comentarios en cada publicación
- Likes y quitar like
- Buscar usuarios, enviar solicitudes de amistad, aceptarlas y ver la lista de amigos

## Rutas

Todas van con el prefijo `/api`. Menos `register` y `login`, todas piden el token en el encabezado `Authorization: Bearer <token>`.

| Método | Ruta | Para qué |
|---|---|---|
| POST | `/register` | Crear una cuenta |
| POST | `/login` | Iniciar sesión y recibir el token |
| POST | `/logout` | Cerrar sesión |
| GET | `/me` | Datos del usuario actual |
| GET, POST | `/posts` | Listar y crear publicaciones |
| GET, DELETE | `/posts/{post}` | Ver o borrar una publicación |
| GET, POST | `/posts/{post}/comments` | Ver y agregar comentarios |
| POST, DELETE | `/posts/{post}/like` | Dar o quitar like |
| GET | `/users/search` | Buscar usuarios |
| POST | `/users/{user}/friend` | Enviar solicitud de amistad |
| GET | `/friendships/pending` | Ver solicitudes pendientes |
| POST | `/friendships/{friendship}/accept` | Aceptar una solicitud |
| GET | `/friends` | Ver mis amigos |

## Tablas

`users`, `profiles`, `posts`, `comments`, `likes`, `friendships` y `personal_access_tokens`.

## Cómo correrla

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```
