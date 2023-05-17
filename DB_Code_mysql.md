---

### **Code used to create the DB** 

``` sql
DROP DATABASE if exists flat_line_v2;
CREATE DATABASE flat_line_v2;
USE flat_line_v2;
#Tables creation: This includes all the tables were our information is going to be stored

#Table with the total of intentional homicides

CREATE TABLE country (
	iso_code_cou	VARCHAR(60) NOT NULL,
    country_ih 		VARCHAR(60) NOT NULL,
    region_ih 		VARCHAR(60) NOT NULL,
    subregion_ih 	VARCHAR(60) NOT NULL,
    CONSTRAINT pk_iso_code_cou PRIMARY KEY (iso_code_cou)
);


#Load of the data in .csv format file.

LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/country.csv' 
 INTO TABLE country
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;

show WARNINGS;

CREATE TABLE year (
  year_cou 		YEAR,
 CONSTRAINT pk_year_cou PRIMARY KEY (year_cou)
);

LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/years.csv' 
 INTO TABLE year
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;


CREATE TABLE sex (
  sex_cou 		VARCHAR(30) NOT NULL,
 CONSTRAINT pk_sex_cou PRIMARY KEY (sex_cou)
);


INSERT INTO sex (sex_cou) VALUES ('Female');
INSERT INTO sex (sex_cou) VALUES ('Male');
INSERT INTO sex (sex_cou) VALUES ('Total');

#Table with violent & Sexual Crime

CREATE TABLE viol_sex_crime (
	iso_code_vsc 	VARCHAR(60) NOT NULL,
    indicator_vsc 	VARCHAR(60) NOT NULL,
    dimension_vsc 	VARCHAR(60) NOT NULL,
    category_vsc 	VARCHAR(90) NOT NULL,
    sex_vsc 		VARCHAR(30) NOT NULL,
    age_vsc 		VARCHAR(60) NOT NULL,
    year_vsc 		YEAR,
    unit_vsc 		VARCHAR(60) NOT NULL,
    value_vsc 		DECIMAL(40 , 10 ),
    source_vsc 		VARCHAR(255),
    
    CONSTRAINT fk_iso_code_vsc  FOREIGN KEY (iso_code_vsc)      REFERENCES  country (iso_code_cou),
    CONSTRAINT fk_sex_vsc  FOREIGN KEY (sex_vsc)        		REFERENCES  sex(sex_cou ),
    CONSTRAINT fk_year_vsc FOREIGN KEY (year_vsc) 				REFERENCES year(year_cou)
);


#Load of the data in .csv format file.
 LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/viol_sex_crime.csv' 
 INTO TABLE viol_sex_crime
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;
 
 #Table with convicted 
 CREATE TABLE persons_held (
	iso_code_ph	VARCHAR(60) NOT NULL,
    indicator_ph 	VARCHAR(60) NOT NULL,
    dimension_ph 	VARCHAR(60) NOT NULL,
    category_ph 	VARCHAR(90) NOT NULL,
    sex_ph 		VARCHAR(30) NOT NULL,
    age_ph 		VARCHAR(60) NOT NULL,
    year_ph 		YEAR,
    unit_ph 		VARCHAR(60) NOT NULL,
    value_ph 		DECIMAL(40 , 10 ),
    source_ph 		VARCHAR(255),
    
   CONSTRAINT fk_iso_code_ph  FOREIGN KEY (iso_code_ph)       REFERENCES  country (iso_code_cou),
   CONSTRAINT fk_sex_ph  FOREIGN KEY (sex_ph)        		REFERENCES  sex(sex_cou ),
   CONSTRAINT fk_year_ph FOREIGN KEY (year_ph) 				REFERENCES year(year_cou)
);

 
 #Load of the data in .csv format file.
 LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/persons_held.csv' 
 INTO TABLE persons_held
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;
 
  #Table with prison death

 CREATE TABLE prison_mortality (
	iso_code_pm	VARCHAR(60) NOT NULL,
    indicator_pm 	VARCHAR(60) NOT NULL,
    dimension_pm 	VARCHAR(60) NOT NULL,
    category_pm 	VARCHAR(90) NOT NULL,
    sex_pm 		VARCHAR(30) NOT NULL,
    age_pm 		VARCHAR(60) NOT NULL,
    year_pm 		YEAR,
    unit_pm 		VARCHAR(60) NOT NULL,
    value_pm 		DECIMAL(40 , 10 ),
    source_pm 		VARCHAR(255),
    
    CONSTRAINT fk_iso_code_pm  FOREIGN KEY (iso_code_pm)       REFERENCES  country (iso_code_cou),
	CONSTRAINT fk_sex_pm  FOREIGN KEY (sex_pm)        		REFERENCES  sex(sex_cou ),
    CONSTRAINT fk_year_pm FOREIGN KEY (year_pm) 				REFERENCES year(year_cou)
); 

 
 #Load of the data in .csv format file.
 LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/prison_mortal.csv' 
 INTO TABLE prison_mortality
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;
 

  CREATE TABLE intent_homicide (
	iso_code_ih	VARCHAR(60) NOT NULL,
    indicator_pm 	VARCHAR(60) NOT NULL,
    dimension_pm 	VARCHAR(60) NOT NULL,
    category_pm 	VARCHAR(90) NOT NULL,
    sex_pm 		VARCHAR(30) NOT NULL,
    age_pm 		VARCHAR(60) NOT NULL,
    year_pm 		YEAR,
    unit_pm 		VARCHAR(60) NOT NULL,
    value_pm 		DECIMAL(40 , 10 ),
    source_pm 		VARCHAR(255),
    
    CONSTRAINT fk_iso_code_ihh  FOREIGN KEY (iso_code_ih)       REFERENCES  country (iso_code_cou),
	CONSTRAINT fk_sex_pm2  FOREIGN KEY (sex_pm)        		REFERENCES  sex(sex_cou ),
    CONSTRAINT fk_year_pm2 FOREIGN KEY (year_pm) 				REFERENCES year(year_cou)
);

 
 #Load of the data in .csv format file.
 LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/inten_homi.csv' 
 INTO TABLE intent_homicide
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;
 
 

  CREATE TABLE traff_persons (
	iso_code_tp	VARCHAR(60) NOT NULL,
    indicator_tp 	VARCHAR(60) NOT NULL,
    dimension_ptp 	VARCHAR(60) NOT NULL,
    category_tp 	VARCHAR(90) NOT NULL,
    sex_tp 		VARCHAR(30) NOT NULL,
    age_tp 		VARCHAR(60) NOT NULL,
    year_tp 		YEAR,
    unit_tp 		VARCHAR(60) NOT NULL,
    value_tp 		VARCHAR(60)  NULL,
    source_tp 		VARCHAR(255),
    
    CONSTRAINT fk_iso_code_tp FOREIGN KEY (iso_code_tp)       REFERENCES  country (iso_code_cou),
	CONSTRAINT fk_sex_tp  FOREIGN KEY (sex_tp)        		REFERENCES  sex(sex_cou ),
    CONSTRAINT fk_year_tp FOREIGN KEY (year_tp) 				REFERENCES year(year_cou)
);

 
 #Load of the data in .csv format file.
 LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/traff_persons.csv' 
 INTO TABLE traff_persons
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;
 
 
 
CREATE TABLE sex_crime (
	iso_code_sc 	VARCHAR(60) NOT NULL,
    indicator_sc 	VARCHAR(60) NOT NULL,
    dimension_sc 	VARCHAR(60) NOT NULL,
    category_sc 	VARCHAR(90) NOT NULL,
    sex_sc 		VARCHAR(30) NOT NULL,
    age_sc 		VARCHAR(60) NOT NULL,
    year_sc 		YEAR,
    unit_sc 		VARCHAR(60) NOT NULL,
    value_sc 		DECIMAL(40 , 10 ),
    source_sc 		VARCHAR(255),
    
    CONSTRAINT fk_iso_code_sc  FOREIGN KEY (iso_code_sc)       REFERENCES  country (iso_code_cou),
	CONSTRAINT fk_sex_sc  FOREIGN KEY (sex_sc)        		REFERENCES  sex(sex_cou ),
    CONSTRAINT fk_year_sc FOREIGN KEY (year_sc) 				REFERENCES year(year_cou)
);


#Load of the data in .csv format file.
 LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/sex_crime.csv' 
 INTO TABLE sex_crime
 FIELDS TERMINATED BY ';'
 LINES TERMINATED BY '\n'
 IGNORE 1 ROWS;

```
