### **Code used to further updates on the DB** 



``` sql
DELIMITER //

CREATE PROCEDURE update_data_from_csv()
BEGIN
  -- Update the 'country' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/country.csv'
    INTO TABLE country
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      country_ih = VALUES(country_ih),
      region_ih = VALUES(region_ih),
      subregion_ih = VALUES(subregion_ih);
      
  -- Update the 'year' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/years.csv'
    INTO TABLE year
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE year_cou = VALUES(year_cou);
  
  -- Update the 'sex' table (assuming you don't have any data changes)
  
  -- Update the 'viol_sex_crime' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/viol_sex_crime.csv'
    INTO TABLE viol_sex_crime
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      indicator_vsc = VALUES(indicator_vsc),
      dimension_vsc = VALUES(dimension_vsc),
      category_vsc = VALUES(category_vsc),
      age_vsc = VALUES(age_vsc),
      unit_vsc = VALUES(unit_vsc),
      value_vsc = VALUES(value_vsc),
      source_vsc = VALUES(source_vsc);
  
  -- Update the 'persons_held' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/persons_held.csv'
    INTO TABLE persons_held
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      indicator_ph = VALUES(indicator_ph),
      dimension_ph = VALUES(dimension_ph),
      category_ph = VALUES(category_ph),
      sex_ph = VALUES(sex_ph),
      age_ph = VALUES(age_ph),
      unit_ph = VALUES(unit_ph),
      value_ph = VALUES(value_ph),
      source_ph = VALUES(source_ph);
      
  -- Update the 'prison_mortality' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/prison_mortal.csv'
    INTO TABLE prison_mortality
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      indicator_pm = VALUES(indicator_pm),
      dimension_pm = VALUES(dimension_pm),
      category_pm = VALUES(category_pm),
      sex_pm = VALUES(sex_pm),
      age_pm = VALUES(age_pm),
      unit_pm = VALUES(unit_pm),
      value_pm = VALUES(value_pm),
      source_pm = VALUES(source_pm);
      
  -- Update the 'intent_homicide' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/inten_homi.csv'
    INTO TABLE intent_homicide
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      indicator_pm = VALUES(indicator_pm),
      dimension_pm = VALUES(dimension_pm),
      category_pm = VALUES(category_pm),
      sex_pm = VALUES(sex_pm),
      age_pm = VALUES(age_pm),
      unit_pm = VALUES(unit_pm),
      value_pm = VALUES(value_pm),
      source_pm = VALUES(source_pm);
      
  -- Update the 'traff_persons' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/traff_persons.csv'
    INTO TABLE traff_persons
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      indicator_tp = VALUES(indicator_tp),
      dimension_ptp = VALUES(dimension_ptp),
      category_tp = VALUES(category_tp),
      sex_tp = VALUES(sex_tp),
      age_tp = VALUES(age_tp),
      unit_tp = VALUES(unit_tp),
      value_tp = VALUES(value_tp),
      source_tp = VALUES(source_tp);
      
  -- Update the 'sex_crime' table
  LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/flat_line_v2/sex_crime.csv'
    INTO TABLE sex_crime
    FIELDS TERMINATED BY ';'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS
    ON DUPLICATE KEY UPDATE
      indicator_sc = VALUES(indicator_sc),
      dimension_sc = VALUES(dimension_sc),
      category_sc = VALUES(category_sc),
      sex_sc = VALUES(sex_sc),
      age_sc = VALUES(age_sc),
      unit_sc = VALUES(unit_sc),
      value_sc = VALUES(value_sc),
      source_sc = VALUES(source_sc);
END //

DELIMITER ;


CALL update_data_from_csv();
