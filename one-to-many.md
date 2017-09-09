### Schema

```
users
    id | name 
    ---------
    1   | Ei Khant Mon
    2   | Kyaw Kyaw

phones
    id | number | user_id
    ------------------------
    1 | 09777777777 | 1
    2 | 09888888888 | 1
    3 | 09111111111  | 2
    4 | 09555555555   | 2
```


### Schema create
```

create table `users` (
    `id` int unsigned not null auto_increment,
    `name` varchar(100) not null,
    primary key(`id`)
);

create table `phones` (
    `id` int unsigned not null auto_increment,
    `user_id` int unsigned,
    `number` varchar(25) not null,
    index phone_user_index(`user_id`),
    foreign key (`user_id`) references users(`id`) on delete set null,
    primary key(`id`)
);

```



### Inser data to users table

INSERT INTO users
    (name)
VALUES
    ('Ei Khant Mon'),
    ('Kyaw Kyaw'),
    ('Min Min');



### Inser data to phones table.


INSERT INTO phones
    (user_id, number)
VALUES
    (1, 09777777777),
    (1, 09888888888),
    (2, 09111111111),
    (2, 09555555555);


### Querying the data.

#### INNER JOIN
```
SELECT users.name, phones.number
FROM `users`
INNER JOIN `phones` on users.id = phones.user_id;
```

#### LEFT JOIN
```
SELECT users.name, phones.number
FROM `users`
LEFT JOIN `phones` on users.id = phones.user_id;
```

#### RIGHT JOIN
```
SELECT users.name, phones.number
FROM `users`
RIGHT JOIN `phones` on users.id = phones.user_id;
```