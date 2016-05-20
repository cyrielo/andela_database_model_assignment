#The Database model for a car booking application
##Below are some of the queries to manipulate the creation of database operations

1. Create a table to store the user informations
```sql
CREATE TABLE `Users` (
  `user_id` INT(11) NOT NULL AUTO_INCREMENT,
  `username` VARCHAR(20) NULL DEFAULT NULL,
  `email` VARCHAR(50) NULL DEFAULT NULL,
  `full_name` VARCHAR(150) NOT NULL,
  `password ` VARCHAR(300) NULL DEFAULT NULL,
  `sex` VARCHAR(10) NULL DEFAULT NULL,
  `avatar` VARCHAR(150) NULL DEFAULT NULL,
  `address` VARCHAR(150) NULL DEFAULT NULL,
  `remember_token` VARCHAR(300) NULL DEFAULT NULL,
  `permission_id` INT(11) NULL DEFAULT NULL,
  `date_added` DATETIME NULL DEFAULT NULL,
  PRIMARY KEY (`user_id`)
) COMMENT 'The user table to store information, of every user';
```

2. When a user make a booking we insert a record into the database
```sql
INSERT INTO `Bookings` (`user_id`,  `date_booked`, `pickup_date`, `dropoff_date`, 
	`pickup_location_id`, `dropoff_location_id`, `car_id`,  `amount_payed`)
VALUES ( [user_id], [date_booked], [pickup_date], [dropoff_date], 
[pickup_location_id], [dropoff_location_id],  [car_id], [amount_payed] );
```

3. When a user makes a successfull debit transaction we update the user's wallet 
details.
```sql
UPDATE `Wallet` SET 
	`balance` = ['new_balance'], `ledger_balance` = ['ledger_balance'], 
	last_debit_date = ['last_debit_date'] WHERE `user_id` = ['user_id']
```

4. When a car is no longer available for booking we remove it from the database
```sql
DELETE FROM `Cars` WHERE `car_id` = ['car_id'];
```

5. When we need to get all latest booking information including users who made the 
booking
```sql
SELECT * FROM `Bookings` 
INNER JOIN `Users`
ON Bookings.user_id = Users.user_id
ORDER BY booking_id DESC;
```