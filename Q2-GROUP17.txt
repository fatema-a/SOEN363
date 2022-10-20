CREATE TABLE movies(
	mid INT PRIMARY KEY, 
	title VARCHAR,
  	year INT,
  	rating REAL,
  	num_ratings INT,
  	UNIQUE(mid, title, year),
  	CHECK(rating >= 0 AND rating <= 5.0)
);

CREATE TABLE actors(
  mid INT REFERENCES movies(mid),
  name VARCHAR,
  cast_position INT,
  PRIMARY KEY(mid,name)
);
 
 CREATE TABLE genres(
   mid INT REFERENCES movies(mid),
   genre VARCHAR,
   PRIMARY KEY(mid,genre)
 );
   
 CREATE TABLE tag_names(
   	tid INT PRIMARY KEY,
   	tag VARCHAR
 );
   
 CREATE TABLE tags(
   	mid INT REFERENCES movies(mid),
   	tid INT REFERENCES tag_names(tid),
   	PRIMARY KEY(mid, tid)
 );
