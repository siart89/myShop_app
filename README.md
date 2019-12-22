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
<td>text</td>
***
Таблица текущих сессий `sessions`
<table>
<tr>
<td>id<td>user_id<td>ip<td>os<td>browser<td>user_agent<td>refresh_token<td>expired_at
<td>created_at<td>name
<tr>
<td>SERIAL PRIMARY KEY
<td>bigint NOT NULLL REFERENCES users (id)
<td>cidr NOT NULL
<td>text 
<td>text
<td>text
<td>text
<td>timestamp with time zone
<td>timestamp with time zone
<td>text</td>

Таблица всех продуктов - книг `books`
<table>
<tr>
<td>id<td>user_id<td>title<td>author<td>description<td>cover<td>price<td>created_at<td>rating<td>category<td>sale
<td>SERIAL PRIMARY KEY
<td>bigint NOT NULLL REFERENCES users (id)
<td>text NOT NULL
<td>text NOT NULL
<td>text NOT NULL
<td>text NOT NULL
<td>money NOT NULL
<td>timestamp with time zone DEFAULT CURRENT_TIMESTAMP
<td>real
<td>text
<td>boolean DEFAULT false</td>

Таблица отзывов - комментариев `comments`
<table>
<tr>
<td>id<td>book_id<td>text<td>created_at<td>is_read<td>author_name<td>rating
<td>SERIAL PRIMARY KEY
<td>bigint REFERENCES books (id) ON DELETE CASCADE
<td>text NOT NULL
<td>timestamp with time zone DEFAULT CURRENT_TIMESTAMP
<td>boolean DEFAULT false
<td>text
<td>smallint</td>

Таблица избранных товаров `favorites`
<table>
<tr>
<td>book_id<td>user_id<id>
<tr>
<td>bigint REFERENCES books (id) ON DELETE CASCADE
<td>bigint REFERENCES users (id) ON DELETE CASCADE
<td>SERIAL PRIMARY KEY</td>


