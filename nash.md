-- Changing the Type of saledate Column

-- SELECT saledate, DATE(saledate) FROM nash_house

-- ALTER TABLE nash_house
-- ADD sale_date_converted DATE

-- UPDATE nash_house
-- SET sale_date_converted = DATE(saledate)

-- SELECT * FROM nash_house

-- Populate Property Address Data

-- SELECT * FROM nash_house
-- WHERE property_address IS NULL
-- ORDER BY parcel_id

-- SELECT n1.parcel_id, COALESCE(n1.property_address, n2.property_address), n2.parcel_id, n2.property_address 
-- FROM nash_house AS n1
-- INNER JOIN nash_house AS n2
-- ON n1.parcel_id = n2.parcel_id AND n1.unique_id <> n2.unique_id 
-- WHERE n1.property_address IS NULL

-- ALTER TABLE nash_house
-- ADD updated_property_address VARCHAR(200)

-- SELECT n1.parcel_id, COALESCE(n1.property_address, n2.property_address), n2.parcel_id, n2.property_address 
-- FROM nash_house AS n1
-- INNER JOIN nash_house AS n2
-- ON n1.parcel_id = n2.parcel_id AND n1.unique_id <> n2.unique_id 
-- WHERE n1.property_address IS NULL


UPDATE nash_house
SET updated_property_address = COALESCE(n1.property_address, n2.property_address) 
                               FROM nash_house AS n1
                               INNER JOIN nash_house AS n2
                               ON n1.parcel_id = n2.parcel_id AND n1.unique_id <> n2.unique_id
