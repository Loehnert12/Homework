# Section 7.1 
## Question 1
```SQL

SELECT ModelYear, Make, Model
FROM EVRegistry

```
## Question 2 
```SQL

SELECT DISTINCT ElectricVehicleType
FROM EVRegistry

```
## Question 3
```SQL

SELECT *
FROM EVRegistry
WHERE ElectricVehicleType = 'Battery Electric Vehicle (BEV)' 

```
## Question 4
```SQL

SELECT Make, Model
FROM EVRegistry
WHERE BaseMSRP BETWEEN 20000 AND 35000 

```

# Section 7.2
## Question 1
```SQL

SELECT *
FROM EVRegistry
WHERE City is NULL

```
## Question 2
```SQL

SELECT Make, Model, ElectricVehicleType
FROM EVRegistry
WHERE VIN like "%3E1EA1J"

```
## Question 3
```SQL

SELECT ModelYear, Make, Model, ElectricVehicleType, ElectricRange
FROM EVRegistry
WHERE (Make= "TESLA") or (Make= "CHEVROLET")
ORDER by Make ASC, ModelYear ASC  

```
## Question 4
```SQL

SELECT StationID, Count(*) as numUses
FROM EVCharging
GROUP BY StationID 
ORDER BY COUNT(*) DESC
LIMIT 5

```
## Question 5
```SQL

SELECT userId, min(chargeTimeHrs) as "minTime", max(chargeTimeHrs) as "maxTime"
FROM EVCharging
WHERE chargeTimeHrs > 0.5
GROUP by userId
ORDER by 2,3

```
# Section 7.3
## Question 1
```SQL

SELECT weekday, round(avg(chargeTimeHrs),2) as 'avgChargeTime'
FROM EVCharging
GROUP by weekday
order by avgChargeTime DESC

```
# Section 7.3
## Question 2
```SQL

SELECT userId, round(sum(kwhTotal),2) as 'totalPower'
FROM EVCharging
group by userId
ORDER by totalPower DESC
LIMIT 15

```
# Section 7.3
## Question 3
```SQL

SELECT dimFacility.typeFacility as typeFacility, count(factCharge.stationId) as numStation
FROM dimFacility, factCharge
WHERE dimFacility.FacilityKey = factCharge.facilityID
GROUP by typeFacility
ORDER by numStation DESC

```
# Section 7.3
## Question 4
### The primary key in a table essentially shows you the unique data in that row. Foreign keys allow you to link data from another table. The foreign key in one table will be a primary key from another table in that data base.


# Section 7.3
## Question 5
```SQL

SELECT userId, min(chargeTimeHrs) as minTime, max(chargeTimeHrs) as maxTime
FROM EVCharging
GROUP by userId
HAVING minTime > 1.0
ORDER by 2 ASC, 3 ASC

```