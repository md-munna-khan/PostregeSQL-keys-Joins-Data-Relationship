Slide Link: https://drive.google.com/file/d/1CpfSPU_WYHSXEg_Yc3H02PZQ9Hsf9kny/view?usp=drive_link



This module dives into the fundamentals of relational database connections using foreign keys and constraints. You’ll learn how to work with different types of SQL joins—Inner, Left, Right, Full, Cross, and Natural—to combine data effectively across tables. To strengthen your skills, we’ve included hands-on SQL practice sessions so you can apply what you’ve learned in real scenarios.

## 47-1 Foreign Key Explained
- Foreign key is one tables primary key is set in another table and makes a relationship
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)

## 47-2 Adding Foreign Key Constraint
```sql
-- user table
create table users (
  id serial primary key,
  username varchar(25) not null
);



-- post table

create table posts (
  id serial primary key,
  title text not null,
  user_id int references "users"(id)
);


insert into users (username) values
('akash'),
('batash'),
('meghna'),
('jamuna')

insert into posts (title,user_id) values
('Enjoyin a sunny day  with akash',2),
('Batahs is the charing',1),
('Exploring adventure with sagor',4),
('you travelling in jamuna',4)
```

## 47-3 Understanding Inner Join
```sql
select * from post
 join users on users.id = post.user_id;
```

- ambiguous error of same id

```sql 
select id,title,username from post
 join users on users.id = post.user_id;
```

- to avoid this error we have to pass context 

```sql 
select post.id,title,username from post
 join users on users.id = post.user_id;
```

```sql 
select p.id, title,username from post as p
 join users as u on  p.user_id = u.id;
```

- this join ais called inner join as well 

```sql 
select p.id, title,username from post as p
inner join users as u on  p.user_id = u.id;
```

![alt text](image-3.png)