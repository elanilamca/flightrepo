# flightrepo

use reservation;

create table user
(
id int not null auto_increment,
first_name varchar(30),
last_name varchar(30),
email varchar(50),
password varchar(75),
primary key (id),
unique key (email)
);


create table flight
(
id int not null auto_increment,
flight_number varchar(20) not null,
operating_airlines varchar(20) not null,
departure_city varchar(20) not null,
arrival_city varchar(20) not null,
date_of_departure date not null,
estimated_departure_time timestamp default current_timestamp,
primary key (id)
);

create table passenger
(
id int not null auto_increment,
first_name varchar(256),
last_name varchar(256),
middle_name varchar(256),
email varchar(50),
phone varchar(10),
primary key (id)
);

create table reservation
(
id int not null auto_increment,
checked_in tinyint(1),
number_of_bags int,
passenger_id int,
flight_id int,
created timestamp default current_timestamp,
primary key (id),
foreign key (passenger_id) references passenger(id) on delete cascade,
foreign key (flight_id) references flight(id)
);

select * from reservation;
select * from user;

select * from flight;
desc flight;
alter table flight drop column fligt_number;

insert into flight values(1,'AA1','American Airlines','AUS','NYC',STR_TO_DATE('02-05-2018','%m-%d-%Y'),'2018-02-05 03:14:07');
insert into flight values(2,'AA2','American Airlines','AUS','NYC',STR_TO_DATE('02-05-2018','%m-%d-%Y'),'2018-02-05 05:14:07');
insert into flight values(3,'AA3','American Airlines','AUS','NYC',STR_TO_DATE('02-05-2018','%m-%d-%Y'),'2018-02-05 06:14:07');
insert into flight values(4,'SW1','South West','AUS','NYC',STR_TO_DATE('02-05-2018','%m-%d-%Y'),'2018-02-05 07:14:07');
insert into flight values(5,'UA1','United Airlines','NYC','DAL',STR_TO_DATE('02-05-2018','%m-%d-%Y'),'2018-02-05 10:14:07');
insert into flight values(6,'UA1','United Airlines','AUS','NYC',STR_TO_DATE('02-06-2018','%m-%d-%Y'),'2018-02-06 07:14:07');

insert into flight values(7,'SW1','South West','AUS','NYC',STR_TO_DATE('02-06-2018','%m-%d-%Y'),'2018-02-06 07:14:07');
insert into flight values(8,'SW1','South West','AUS','NYC',STR_TO_DATE('02-06-2018','%m-%d-%Y'),'2018-02-05 08:14:07');
insert into flight values(9,'SW3','South West','NYC','DAL',STR_TO_DATE('02-06-2018','%m-%d-%Y'),'2018-02-06 10:14:07');
insert into flight values(10,'UA1','United Airlines','NYC','DAL',STR_TO_DATE('02-06-2018','%m-%d-%Y'),'2018-02-06 10:14:07');


select flight0_.id as id1_0_, 
flight0_.arrival_city as arrival_2_0_, 
flight0_.date_of_departure as date_of_3_0_, 
flight0_.departure_city as departur4_0_, 
flight0_.estimated_departure_time as estimate5_0_, 
flight0_.fligt_number as fligt_nu6_0_, 
flight0_.operating_airlines as operatin7_0_ 
from flight flight0_ 
where flight0_.departure_city='AUS' and flight0_.arrival_city='NYC';

select flight0_.id as id1_0_, 
flight0_.arrival_city as arrival_2_0_, 
flight0_.date_of_departure as date_of_3_0_, 
flight0_.departure_city as departur4_0_, 
flight0_.estimated_departure_time as estimate5_0_, 
flight0_.fligt_number as fligt_nu6_0_, 
flight0_.operating_airlines as operatin7_0_  
from flight flight0_ 
where flight0_.departure_city='AUS'
and flight0_.arrival_city='NYC' 
and flight0_.date_of_departure='2018-02-05';

select * from reservation;
select * from passenger;
select * from role;

create table Role
(
ID INT NOT NULL auto_increment,
NAME varchar(20),
primary key (ID)
);

create table user_role
(
user_id int,
role_id int,
foreign key (user_id)
references user(id),
foreign key (role_id)
references role(id)
);

select * from user_role;
select * from role;
select * from user;
delete from user;

insert into role values(1,'ADMIN');
insert into user_role values(1,1);

drop table user_role;

drop table role;
