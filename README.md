# Project-8--Code-First-Girls-SQL
Code First Girls (UK Based) Organization- SQL Project-

* Created Relational Database (6 Tables)
* Set Primary Key and Foriegn Key Constraints to create relations between the Tables
* Create JOIN which combines multiple tables in a logical way
* Created a stored function
* Preparaed Query with a subquery to extract data from Database for analysis
* Create an ER Diagram where all table relations are shown
* Created a stored procedure
* Used Group BY, Having, Order BY, JOIN functions to query database

# Code for SQL Query 

-- MySQL dump 10.13  Distrib 8.0.36, for Win64 (x86_64)
--
-- Host: localhost    Database: employeesdatabase
-- ------------------------------------------------------
-- Server version	8.0.36

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `departments`
--

DROP TABLE IF EXISTS `departments`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `departments` (
  `dept_no` int NOT NULL,
  `dept_name` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`dept_no`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `departments`
--

LOCK TABLES `departments` WRITE;
/*!40000 ALTER TABLE `departments` DISABLE KEYS */;
INSERT INTO `departments` VALUES (101,'Marketing'),(102,'Finance'),(103,'Human Resources'),(104,'Production'),(105,'Development'),(106,'Quality Management'),(107,'Sales'),(108,'Research'),(109,'Customer Service');
/*!40000 ALTER TABLE `departments` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `dept_employee`
--

DROP TABLE IF EXISTS `dept_employee`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `dept_employee` (
  `emp_no` int NOT NULL,
  `dept_no` int NOT NULL,
  `from_date` date NOT NULL,
  `to_date` date NOT NULL,
  KEY `emp_no` (`emp_no`),
  KEY `dept_no` (`dept_no`),
  CONSTRAINT `dept_employee_ibfk_1` FOREIGN KEY (`emp_no`) REFERENCES `employees` (`emp_no`),
  CONSTRAINT `dept_employee_ibfk_2` FOREIGN KEY (`dept_no`) REFERENCES `departments` (`dept_no`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `dept_employee`
--

LOCK TABLES `dept_employee` WRITE;
/*!40000 ALTER TABLE `dept_employee` DISABLE KEYS */;
INSERT INTO `dept_employee` VALUES (2,104,'2012-07-03','2018-10-25'),(4,105,'2015-10-20','2017-11-21'),(6,106,'2015-05-25','2019-10-24'),(8,109,'2017-02-24','2019-08-12'),(10,104,'2022-03-31','2022-12-30'),(1,101,'2011-10-11','2012-12-28'),(2,102,'2018-10-26','2019-12-20'),(3,103,'2016-04-27','2018-02-20'),(4,104,'2010-08-07','2015-10-19'),(5,105,'2013-05-20','2015-10-19'),(6,106,'2014-02-24','2015-05-24'),(7,107,'2020-07-15','2021-11-14'),(8,108,'2017-01-09','2019-11-14'),(9,109,'2019-11-30','2020-05-25'),(10,104,'2021-12-08','2022-04-01');
/*!40000 ALTER TABLE `dept_employee` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `dept_manager`
--

DROP TABLE IF EXISTS `dept_manager`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `dept_manager` (
  `emp_no` int NOT NULL,
  `dept_no` int NOT NULL,
  `from_date` date NOT NULL,
  `to_date` date NOT NULL,
  KEY `emp_no` (`emp_no`),
  KEY `dept_no` (`dept_no`),
  CONSTRAINT `dept_manager_ibfk_1` FOREIGN KEY (`emp_no`) REFERENCES `employees` (`emp_no`),
  CONSTRAINT `dept_manager_ibfk_2` FOREIGN KEY (`dept_no`) REFERENCES `departments` (`dept_no`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `dept_manager`
--

LOCK TABLES `dept_manager` WRITE;
/*!40000 ALTER TABLE `dept_manager` DISABLE KEYS */;
INSERT INTO `dept_manager` VALUES (1,101,'2012-05-18','2015-08-12'),(3,107,'2017-04-28','2019-07-22'),(5,103,'2014-11-24','2018-12-12'),(7,102,'2020-09-20','2021-08-15'),(9,108,'2019-10-20','2020-06-26'),(1,102,'2011-10-11','2012-12-28'),(2,103,'2018-10-26','2019-12-20'),(3,104,'2016-04-27','2018-02-20'),(4,105,'2010-08-07','2015-10-19'),(5,106,'2013-05-20','2015-10-19'),(6,107,'2014-02-24','2015-05-24'),(7,108,'2020-07-15','2021-11-14'),(8,109,'2017-01-09','2019-11-14'),(9,109,'2019-11-30','2020-05-25'),(10,101,'2021-12-08','2022-04-01');
/*!40000 ALTER TABLE `dept_manager` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `employees`
--

DROP TABLE IF EXISTS `employees`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `employees` (
  `emp_no` int NOT NULL,
  `birth_date` date NOT NULL,
  `first_name` varchar(50) NOT NULL,
  `last_name` varchar(50) NOT NULL,
  `gender` varchar(1) NOT NULL,
  `hire_date` date NOT NULL,
  PRIMARY KEY (`emp_no`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `employees`
--

LOCK TABLES `employees` WRITE;
/*!40000 ALTER TABLE `employees` DISABLE KEYS */;
INSERT INTO `employees` VALUES (1,'1987-10-24','Scarlet','Roth','F','2011-10-11'),(2,'1986-12-08','Veronica','Reth','F','2012-07-02'),(3,'1996-05-23','John','Green','M','2016-04-27'),(4,'1989-07-20','James','Dashner','M','2010-08-07'),(5,'1991-01-02','Markus','Zusak','M','2013-05-20'),(6,'1990-01-13','Cassandra','Clare','F','2014-02-24'),(7,'1987-06-30','Suzanne','Collins','F','2020-07-15'),(8,'1997-09-10','Rick','Riordan','M','2017-01-09'),(9,'1992-04-19','Jennifier','Barnes','F','2018-11-30'),(10,'1994-03-28','Leign','Bardugo','M','2021-12-08');
/*!40000 ALTER TABLE `employees` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `salaries`
--

DROP TABLE IF EXISTS `salaries`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `salaries` (
  `emp_no` int NOT NULL,
  `salary` int NOT NULL,
  `from_date` date NOT NULL,
  `to_date` date NOT NULL,
  KEY `emp_no` (`emp_no`),
  CONSTRAINT `salaries_ibfk_1` FOREIGN KEY (`emp_no`) REFERENCES `employees` (`emp_no`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `salaries`
--

LOCK TABLES `salaries` WRITE;
/*!40000 ALTER TABLE `salaries` DISABLE KEYS */;
INSERT INTO `salaries` VALUES (1,55586,'2011-10-11','2014-08-25'),(2,57195,'2012-07-02','2014-10-12'),(3,58209,'2016-04-27','2017-11-23'),(4,57770,'2010-08-07','2014-02-21'),(5,59188,'2013-05-20','2015-04-10'),(6,60763,'2014-02-24','2016-09-29'),(7,64797,'2020-07-15','2021-09-20'),(8,68037,'2017-01-09','2019-10-12'),(9,69404,'2018-11-30','2020-11-21'),(10,70575,'2021-12-08','2022-10-13'),(1,70464,'2014-08-26','2016-05-22'),(2,72343,'2014-10-13','2016-09-08'),(3,74365,'2017-11-24','2019-12-03'),(4,74957,'2014-02-22','2018-07-11'),(5,66591,'2015-04-11','2020-10-14');
/*!40000 ALTER TABLE `salaries` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `title`
--

DROP TABLE IF EXISTS `title`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `title` (
  `emp_no` int NOT NULL,
  `title` varchar(50) NOT NULL,
  `from_date` date NOT NULL,
  `to_date` date NOT NULL,
  PRIMARY KEY (`title`),
  KEY `emp_no` (`emp_no`),
  CONSTRAINT `title_ibfk_1` FOREIGN KEY (`emp_no`) REFERENCES `employees` (`emp_no`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `title`
--

LOCK TABLES `title` WRITE;
/*!40000 ALTER TABLE `title` DISABLE KEYS */;
INSERT INTO `title` VALUES (3,'Development Officer','2016-04-27','2019-06-26'),(4,'Engineer','2010-08-07','2015-10-23'),(4,'Executive Engineer','2015-10-24','2017-09-12'),(6,'Executive Finance','2014-02-24','2016-12-25'),(6,'Finance Manager','2016-12-26','2019-11-20'),(5,'Jr. HR','2013-05-20','2015-10-25'),(9,'Marketing Head','2018-11-30','2020-02-12'),(10,'Operations Incharge','2021-12-08','2022-05-25'),(10,'Operations Manager','2022-05-26','2022-12-23'),(7,'Researcher','2020-07-15','2021-10-12'),(8,'Sales Manager','2017-01-09','2019-06-22'),(1,'Senior Engineer','2011-10-11','2015-05-25'),(5,'Sr. HR','2015-10-26','2018-12-11'),(2,'Staff','2012-07-02','2015-10-22');
/*!40000 ALTER TABLE `title` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Dumping routines for database 'employeesdatabase'
--
/*!50003 DROP FUNCTION IF EXISTS `Full_Name` */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
CREATE DEFINER=`root`@`localhost` FUNCTION `Full_Name`(first_name varchar(50), last_name varchar(50)) RETURNS varchar(55) CHARSET utf8mb4
    DETERMINISTIC
RETURN concat(first_name, ' ', last_name) ;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!50003 DROP PROCEDURE IF EXISTS `get_employees` */;
/*!50003 SET @saved_cs_client      = @@character_set_client */ ;
/*!50003 SET @saved_cs_results     = @@character_set_results */ ;
/*!50003 SET @saved_col_connection = @@collation_connection */ ;
/*!50003 SET character_set_client  = utf8mb4 */ ;
/*!50003 SET character_set_results = utf8mb4 */ ;
/*!50003 SET collation_connection  = utf8mb4_0900_ai_ci */ ;
/*!50003 SET @saved_sql_mode       = @@sql_mode */ ;
/*!50003 SET sql_mode              = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION' */ ;
DELIMITER ;;
CREATE DEFINER=`root`@`localhost` PROCEDURE `get_employees`()
BEGIN
   SELECT * FROM employeesdatabase.employees;
END ;;
DELIMITER ;
/*!50003 SET sql_mode              = @saved_sql_mode */ ;
/*!50003 SET character_set_client  = @saved_cs_client */ ;
/*!50003 SET character_set_results = @saved_cs_results */ ;
/*!50003 SET collation_connection  = @saved_col_connection */ ;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2024-03-31 19:08:41

![project_er_diagram](https://github.com/SHEETAL0812/Project-8--Code-First-Girls-SQL/assets/128026212/95a9ef6a-c5f0-4ed4-a663-963af42bc4e9)

