# СУБД:
Используемая СУБД postgreSQL

Структура базы данных имеет слудующий вид:

Таблица пользователей `users`
<table>
<tr>
<td>id<td>name<td>mail<td>password<td>created_at<td>avatar<td>phone
<tr>
<td>SERIAL PRIMARY KEY
<td>text NOT NULL
<td>text NOT NULL
<td>text NOT NULL
<td>timestamp with time zone DEFAULT CURRENT_TIMESTAMP
<td>text
<td>text
