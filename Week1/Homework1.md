Here is the SQL code i used for the questions. 


3
SELECT  
count(1)

FROM taxi_trips_2019
WHERE  CAST(lpep_pickup_datetime AS DATE) = '2019-01-15'



4

SELECT 
	CAST(lpep_pickup_datetime AS DATE) as "Day",
	MAX(trip_distance)

FROM taxi_trips_2019

GROUP BY 
	CAST(lpep_pickup_datetime AS DATE)

ORDER by MAX(trip_distance) desc



5

SELECT 
passenger_count, 
count(passenger_count)

FROM taxi_trips_2019
WHERE  CAST(lpep_pickup_datetime AS DATE) = '2019-01-01'
GROUP BY
 passenger_count



6

SELECT 
	lpep_pickup_datetime,
	lpep_dropoff_datetime,
	tip_amount,
	CONCAT(zpu."Borough", '/', zpu."Zone" ) AS "pick_up_loc" ,
	CONCAT(zdo."Borough",'/', zdo."Zone") AS "dropoff_loc"
FROM 
 taxi_trips_2019 t, 
 zones zpu, 
 zones zdo

WHERE  
	t."PULocationID" = zpu."LocationID" AND 
	t."DOLocationID" = zdo."LocationID" AND
	zpu."Zone" = 'Astoria'

ORDER BY tip_amount desc


