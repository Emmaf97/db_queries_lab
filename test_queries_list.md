CREATE TABLE bookings (
    bookid integer NOT NULL,
    facid integer NOT NULL,
    memid integer NOT NULL,
    starttime timestamp without time zone NOT NULL,
    slots integer NOT NULL
);

CREATE TABLE facilities (
    facid integer NOT NULL,
    name character varying(100) NOT NULL,
    membercost numeric NOT NULL,
    guestcost numeric NOT NULL,
    initialoutlay numeric NOT NULL,
    monthlymaintenance numeric NOT NULL
);

CREATE TABLE members (
    memid integer NOT NULL,
    surname character varying(200) NOT NULL,
    firstname character varying(200) NOT NULL,
    address character varying(300) NOT NULL,
    zipcode integer NOT NULL,
    telephone character varying(20) NOT NULL,
    recommendedby integer,
    joindate timestamp without time zone NOT NULL
);


ALTER TABLE ONLY bookings
    ADD CONSTRAINT bookings_pk PRIMARY KEY (bookid);
	
ALTER TABLE ONLY facilities
    ADD CONSTRAINT facilities_pk PRIMARY KEY (facid);
	
DROP TABLE IF EXISTS bookings;

CREATE TABLE bookings (
    bookid integer NOT NULL,
    facid integer NOT NULL REFERENCES facilities(facid),
    memid integer NOT NULL,
    starttime timestamp without time zone NOT NULL,
    slots integer NOT NULL
);

ALTER TABLE ONLY bookings
    ADD CONSTRAINT fk_bookings_facid FOREIGN KEY (facid) REFERENCES facilities(facid);
