-- 2.
-- Manually create the tables cd.facilities and cd.members 
-- shown at the URL above (make cd.bookings too if you like)

```CREATE TABLE cd.members```
<br>
```    ( ```
<br>
```      memid integer NOT NULL, ```
<br>
```      surname character varying(200) NOT NULL, ```
<br>
```      firstname character varying(200) NOT NULL, ```
<br>
```      address character varying(300) NOT NULL, ```
<br>
```      zipcode integer NOT NULL, ```
<br>
```      telephone character varying(20) NOT NULL, ```
<br>
```      recommendedby integer,```
<br>
```      joindate timestamp NOT NULL,```
<br>
```      CONSTRAINT members_pk PRIMARY KEY (memid),```
<br>
```      CONSTRAINT fk_members_recommendedby FOREIGN KEY (recommendedby)```
<br>
```      REFERENCES cd.members(memid) ON DELETE SET NULL ```
<br>
```    ); ```
<br>
    
``` CREATE TABLE cd.facilities ```
<br>
```   ( ```
<br>
```       facid integer NOT NULL, ```
<br>
```       name character varying(100) NOT NULL, ```
<br>
```       membercost numeric NOT NULL, ```
<br>
```       guestcost numeric NOT NULL, ```
<br>
```       initialoutlay numeric NOT NULL, ```
<br>
```       monthlymaintenance numeric NOT NULL, ```
<br>
```       CONSTRAINT facilities_pk PRIMARY KEY (facid)```
<br>
```    );```
    
``` CREATE TABLE cd.bookings ```
<br>
 ```   (```
 <br>
 ```      bookid integer NOT NULL, ```
 <br>
```       facid integer NOT NULL, ```
<br>
```       memid integer NOT NULL, ```
<br>
```       starttime timestamp NOT NULL,```
<br>
```       slots integer NOT NULL,```
<br>
```       CONSTRAINT bookings_pk PRIMARY KEY (bookid),```
<br>
```       CONSTRAINT fk_bookings_facid FOREIGN KEY (facid) REFERENCES cd.facilities(facid),```
<br>
```       CONSTRAINT fk_bookings_memid FOREIGN KEY (memid) REFERENCES cd.members(memid)```
<br>
```    );```
    
-- 2.a: For each table (facilities/members/bookings)
--	Explain what can... and what can't... happen?
--  {NOTE: ignore and references to 'FOREIGN KEY' for now]

-- 2.b: Do a SELCT * on each and see NO Data yet.
No entries added yet

-- Scroll-down
-- and use the INSERTs for facilities and members
-- to populate those tables with some data
-- and figure out what query to run
--  test it on your local clubdata tables

``` INSERT INTO facilities (facid, name, membercost, guestcost, initialoutlay, monthlymaintenance) VALUES ```
<br>
``` (0, 'Tennis Court 1', 5, 25, 10000, 200),```
<br>
``` (1, 'Tennis Court 2', 5, 25, 8000, 200),```
<br>
``` (2, 'Badminton Court', 0, 15.5, 4000, 50),```
<br>
``` (3, 'Table Tennis', 0, 5, 320, 10),```
<br>
``` (4, 'Massage Room 1', 35, 80, 4000, 3000),```
<br>
``` (5, 'Massage Room 2', 35, 80, 4000, 3000),```
<br>
``` (6, 'Squash Court', 3.5, 17.5, 5000, 80),```
<br>
``` (7, 'Snooker Table', 0, 5, 450, 15),```
<br>
``` (8, 'Pool Table', 0, 5, 400, 15);```
<br>

``` INSERT INTO members (memid, surname, firstname, address, zipcode, telephone, recommendedby, joindate) VALUES```
<br>
```(0, 'GUEST', 'GUEST', 'GUEST', 0, '(000) 000-0000', NULL, '2012-07-01 00:00:00'),```
<br>
```(1, 'Smith', 'Darren', '8 Bloomsbury Close, Boston', 4321, '555-555-5555', NULL, '2012-07-02 12:02:05'),```
<br>
```(2, 'Smith', 'Tracy', '8 Bloomsbury Close, New York', 4321, '555-555-5555', NULL, '2012-07-02 12:08:23'),```
<br>
```(3, 'Rownam', 'Tim', '23 Highway Way, Boston', 23423, '(844) 693-0723', NULL, '2012-07-03 09:32:15'),```
<br>
```(4, 'Joplette', 'Janice', '20 Crossing Road, New York', 234, '(833) 942-4710', 1, '2012-07-03 10:25:05'),```
<br>
```(5, 'Butters', 'Gerald', '1065 Huntingdon Avenue, Boston', 56754, '(844) 078-4130', 1, '2012-07-09 10:44:09'),```
<br>
```(6, 'Tracy', 'Burton', '3 Tunisia Drive, Boston', 45678, '(822) 354-9973', NULL, '2012-07-15 08:52:55'),```
<br>
```(7, 'Dare', 'Nancy', '6 Hunting Lodge Way, Boston', 10383, '(833) 776-4001', 4, '2012-07-25 08:59:12'),```
<br>
```(8, 'Boothe', 'Tim', '3 Bloomsbury Close, Reading, 00234', 234, '(811) 433-2547', 3, '2012-07-25 16:02:35'),```
<br>
```(9, 'Stibbons', 'Ponder', '5 Dragons Way, Winchester', 87630, '(833) 160-3900', 6, '2012-07-25 17:09:05'),```
<br>
```(10, 'Owen', 'Charles', '52 Cheshire Grove, Winchester, 28563', 28563, '(855) 542-5251', 1, '2012-08-03 19:42:37'),```
<br>
```(11, 'Jones', 'David', '976 Gnats Close, Reading', 33862, '(844) 536-8036', 4, '2012-08-06 16:32:55'),```
<br>
```(12, 'Baker', 'Anne', '55 Powdery Street, Boston', 80743, '844-076-5141', 9, '2012-08-10 14:23:22'),```
<br>
```(13, 'Farrell', 'Jemima', '103 Firth Avenue, North Reading', 57392, '(855) 016-0163', NULL, '2012-08-10 14:28:01'),```
<br>
```(14, 'Smith', 'Jack', '252 Binkington Way, Boston', 69302, '(822) 163-3254', 1, '2012-08-10 16:22:05'),```
<br>
```(15, 'Bader', 'Florence', '264 Ursula Drive, Westford', 84923, '(833) 499-3527', 9, '2012-08-10 17:52:03'),```
<br>
```(16, 'Baker', 'Timothy', '329 James Street, Reading', 58393, '833-941-0824', 13, '2012-08-15 10:34:25'),```
<br>
```(17, 'Pinker', 'David', '5 Impreza Road, Boston', 65332, '811 409-6734', 13, '2012-08-16 11:32:47'),```
<br>
```(20, 'Genting', 'Matthew', '4 Nunnington Place, Wingfield, Boston', 52365, '(811) 972-1377', 5, '2012-08-19 14:55:55'),```
<br>
```(21, 'Mackenzie', 'Anna', '64 Perkington Lane, Reading', 64577, '(822) 661-2898', 1, '2012-08-26 09:32:05'),```
<br>
```(22, 'Coplin', 'Joan', '85 Bard Street, Bloomington, Boston', 43533, '(822) 499-2232', 16, '2012-08-29 08:32:41'),```
<br>
```(24, 'Sarwin', 'Ramnaresh', '12 Bullington Lane, Boston', 65464, '(822) 413-1470', 15, '2012-09-01 08:44:42'),```
<br>
```(26, 'Jones', 'Douglas', '976 Gnats Close, Reading', 11986, '844 536-8036', 11, '2012-09-02 18:43:05'),```
<br>
```(27, 'Rumney', 'Henrietta', '3 Burkington Plaza, Boston', 78533, '(822) 989-8876', 20, '2012-09-05 08:42:35'),```
<br>
```(28, 'Farrell', 'David', '437 Granite Farm Road, Westford', 43532, '(855) 755-9876', NULL, '2012-09-15 08:22:05'),```
<br>
```(29, 'Worthington-Smyth', 'Henry', '55 Jagbi Way, North Reading', 97676, '(855) 894-3758', 2, '2012-09-17 12:27:15'),```
<br>
```(30, 'Purview', 'Millicent', '641 Drudgery Close, Burnington, Boston', 34232, '(855) 941-9786', 2, '2012-09-18 19:04:01'),```
<br>
```(33, 'Tupperware', 'Hyacinth', '33 Cheerful Plaza, Drake Road, Westford', 68666, '(822) 665-5327', NULL, '2012-09-18 19:32:05'),```
<br>
```(35, 'Hunt', 'John', '5 Bullington Lane, Boston', 54333, '(899) 720-6978', 30, '2012-09-19 11:32:45'),```
<br>
```(36, 'Crumpet', 'Erica', 'Crimson Road, North Reading', 75655, '(811) 732-4816', 2, '2012-09-22 08:36:38'),```
<br>
```(37, 'Smith', 'Darren', '3 Funktown, Denzington, Boston', 66796, '(822) 577-3541', NULL, '2012-09-26 18:08:45');```


-- 3.
-- ## Follow this tutorial:
-- https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-date/
Completed tutorial


-- 4. 
-- ## Write the statement to 
-- ## DROP THE bookings table IF it exists
<br>
```DROP bookings if EXISTS:```

-- 5.
-- ## Recreate it and populate it with 
-- ## these limited inserts
<br>
```CREATE TABLE bookings ( ```
```bookid integer,```
```facid integer,```
```memid integer,```
```starttime DATE,```
```slots integer);```



```INSERT INTO bookings (bookid, facid, memid, starttime, slots) VALUES```
<br>
```(0, 3, 1, '2012-07-03 11:00:00', 2),```
<br>
```(1, 4, 1, '2012-07-03 08:00:00', 2),```
<br>
```(2, 6, 0, '2012-07-03 18:00:00', 2),```
<br>
```(3, 7, 1, '2012-07-03 19:00:00', 2),```
<br>
```(4, 8, 1, '2012-07-03 10:00:00', 1),```
<br>
```(5, 8, 1, '2012-07-03 15:00:00', 1),```
<br>
```(6, 0, 2, '2012-07-04 09:00:00', 3),```
<br>
```(7, 0, 2, '2012-07-04 15:00:00', 3),```
<br>
```(8, 4, 3, '2012-07-04 13:30:00', 2),```
<br>
```(9, 4, 0, '2012-07-04 15:00:00', 2);```


-- 5. 
-- ## Rename the table to 'booking' (singular)
<br> 
```ALTER TABLE bookings RENAME TO booking;```


-- 6.
-- ## Remove the column 'memid' 
<br> 
```ALTER TABLE booking DROP memid;```


-- 7.
-- ## assume a 'slot' is 20 minutes long...
-- ## Add an 'end_time' column that shows 
-- ## the 'starttime' with the number-of 'slots'
-- ## from the 'slots' column times 20minutes
<br>
```ALTER TABLE booking```
<br>
```ADD COLUMN end_time TIMESTAMP;```
<br>
```UPDATE booking SET end_time = starttime + INTERVAL '20 minutes' * slots;```


-- 8.
-- ## Add a column 'payment_status'
-- ## and fill it with the value 'paid'
<br>
```ALTER TABLE booking```
<br>
```ADD COLUMN payment_status TEXT;```
<br>
```UPDATE booking SET payment_status = 'paid'```

-- 9.
-- ## Put a constraint on the 'payment_status'
-- ## so that it can only store values
-- ## 'paid', 'un-paid' or  'chase-up'

<br>

```ADD CONSTRAINT check_payment_status CHECK (payment_status IN ('paid', 'unpaid', 'chase-up'));```
```SELECT * FROM booking WHERE bookid = 3```
<br>
```UPDATE booking SET payment_status = 'chase-up' ```
<br>
```WHERE bookid = 3;```

-- 10.
-- ## Write a statement(s) to test the 
-- ## constraint is in effect.
-- ## (How could you use the psql cmd-line tool to check this?)

<br>

```SELECT * FROM booking WHERE bookid = 3```
<br>
```UPDATE booking SET payment_status = '' ```
<br>
```WHERE bookid = 1;```


-- 11.
-- ## Rename the column 'starttime' to 'start_time'
<br> 
```ALTER TABLE booking RENAME starttime TO start_time```


-- 12.
-- ## Change the column 'payment_status' to have be
-- ## of type VARCHAR(7);
<br> 
```ALTER TABLE booking ALTER COLUMN payment_status TYPE VARCHAR(7);```

-- 13.
-- ## Make the booking table 'facid' be a 
-- ## foreign-key to the facilities table 'facid'
-- ## (Make a note of what had to be done to achieve this)

-- 14.
-- ## Write a statement(s) to show the effect
-- ## of making booking.facid a foreign-key.

-- 15.
-- ## Make and test a constraint to the effect 
-- ## that if you delete a record or 
-- ## update the 'facid' column value of facilities
-- ## the update/delete propogates to all 
-- ## referencing values in the booking table.

-- 16.
-- ## Make and test a constraint to the effect
-- ## that if the facilities.facid value is updated
-- ## any referencing values in booking.facid
-- ## are set to null

-- 17.
-- ## Repeat 16 for a delete of a record 
-- ## in the facilities.facid

-- 18. 
-- ## Repeat 16 and 17 so that instead of
-- ## referring values being set to null
-- ## they are set to some sensible 
-- ## default value.
