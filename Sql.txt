-- phpMyAdmin SQL Dump
-- version 5.1.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Generation Time: Mar 30, 2022 at 01:02 PM
-- Server version: 10.4.22-MariaDB
-- PHP Version: 8.1.1

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `hospital1`
--

-- --------------------------------------------------------

--
-- Table structure for table `bill`
--

CREATE TABLE `bill` (
  `bill_id` bigint(20) NOT NULL,
  `bill_amount` double DEFAULT NULL,
  `bill_date` date DEFAULT NULL,
  `bill_ins` bit(1) DEFAULT NULL,
  `ins_no` bigint(20) DEFAULT NULL,
  `pid` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `bill`
--

INSERT INTO `bill` (`bill_id`, `bill_amount`, `bill_date`, `bill_ins`, `ins_no`, `pid`) VALUES
(1, 4700, '2022-03-29', b'1', 1234502, 602),
(2, 45000, '2022-03-22', b'1', 1234501, 601),
(123452, 758555, '2022-03-26', b'1', 1234502, 123452),
(123453, 20000, '2022-03-26', b'1', 1234501, 123454),
(123454, 45214, '2022-03-30', b'1', 1234502, 123453);

-- --------------------------------------------------------

--
-- Table structure for table `department`
--

CREATE TABLE `department` (
  `dep_id` bigint(20) NOT NULL,
  `dep_name` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `department`
--

INSERT INTO `department` (`dep_id`, `dep_name`) VALUES
(101, 'ORTHOPEDICS'),
(102, 'CARDIOLOGY'),
(103, 'Anesthesiologists'),
(104, 'Colon and Rectal Surgeons'),
(105, 'Dermatologists'),
(106, 'Endocrinologists'),
(107, 'Gastroenterologists'),
(108, 'Veterinarian');

-- --------------------------------------------------------

--
-- Table structure for table `doctor`
--

CREATE TABLE `doctor` (
  `doc_id` bigint(20) NOT NULL,
  `doc_address` varchar(255) DEFAULT NULL,
  `doc_name` varchar(255) DEFAULT NULL,
  `phone_no` bigint(20) DEFAULT NULL,
  `dep_id` bigint(20) DEFAULT NULL,
  `spec_id` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `doctor`
--

INSERT INTO `doctor` (`doc_id`, `doc_address`, `doc_name`, `phone_no`, `dep_id`, `spec_id`) VALUES
(201, 'Mumbai', 'Dr. Aggarwal Supriya', 8542635825, 102, 402),
(202, 'Mumbai', 'Dr. Aggarwal Arun Kumar', 9587456325, 101, 401),
(203, 'Jamtara', 'Dr. Agnihotri Basant Kumar', 9856321478, 102, 401),
(204, 'Delhi', 'Dr. Yadvendra Singh Baghel', 9658745236, 105, 410),
(205, 'Pune', 'Amruta', 7854123698, 106, 405);

-- --------------------------------------------------------

--
-- Table structure for table `employee`
--

CREATE TABLE `employee` (
  `emp_id` bigint(20) NOT NULL,
  `emp_address` varchar(255) DEFAULT NULL,
  `emp_mobile` bigint(20) DEFAULT NULL,
  `emp_name` varchar(255) DEFAULT NULL,
  `dep_id` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `employee`
--

INSERT INTO `employee` (`emp_id`, `emp_address`, `emp_mobile`, `emp_name`, `dep_id`) VALUES
(101, 'Mumbai', 8456258985, 'Ramesh', 102),
(102, 'Mumbai', 9856325896, 'Rakesh', 101),
(103, 'Ranchi', 8523478564, 'Aman', 105),
(104, 'Kolkata', 6985325698, 'Himanshu', 104);

-- --------------------------------------------------------

--
-- Table structure for table `insurance`
--

CREATE TABLE `insurance` (
  `ins_no` bigint(20) NOT NULL,
  `ins_amt` double DEFAULT NULL,
  `ins_expiry` varchar(255) DEFAULT NULL,
  `pid` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `insurance`
--

INSERT INTO `insurance` (`ins_no`, `ins_amt`, `ins_expiry`, `pid`) VALUES
(1234501, 499999, '2022-03-19', 601),
(1234502, 300000, '2026', 602),
(1234503, 1234503, '2022-03-04', 123454);

-- --------------------------------------------------------

--
-- Table structure for table `medicos`
--

CREATE TABLE `medicos` (
  `med_id` bigint(20) NOT NULL,
  `med_date` date DEFAULT NULL,
  `med_record` varchar(255) DEFAULT NULL,
  `med_price` int(11) DEFAULT NULL,
  `med_quantity` int(11) DEFAULT NULL,
  `med_total` bigint(20) DEFAULT NULL,
  `doc_id` bigint(20) DEFAULT NULL,
  `pid` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `medicos`
--

INSERT INTO `medicos` (`med_id`, `med_date`, `med_record`, `med_price`, `med_quantity`, `med_total`, `doc_id`, `pid`) VALUES
(1, '2022-03-03', 'Augmentin 625 Duo Tablet update', 65, 15, 975, 205, 123456),
(2, '2022-03-04', 'Paracetamol', 78, 10, 780, 203, 123453),
(3, '2022-03-08', 'Tramadol', 99, 16, 1584, 204, 123454),
(5, '2022-02-11', 'Allopurinol ', 150, 10, 1500, 202, 123454);

-- --------------------------------------------------------

--
-- Table structure for table `operation`
--

CREATE TABLE `operation` (
  `op_id` bigint(20) NOT NULL,
  `op_name` varchar(255) DEFAULT NULL,
  `doc_id` bigint(20) DEFAULT NULL,
  `pid` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `operation`
--

INSERT INTO `operation` (`op_id`, `op_name`, `doc_id`, `pid`) VALUES
(301, 'Appendectomy', 201, 601),
(302, 'Breast biopsy', 201, 601);

-- --------------------------------------------------------

--
-- Table structure for table `patient`
--

CREATE TABLE `patient` (
  `pid` bigint(20) NOT NULL,
  `padd` varchar(255) DEFAULT NULL,
  `pdob` varchar(255) DEFAULT NULL,
  `pmobile` bigint(20) DEFAULT NULL,
  `pname` varchar(255) DEFAULT NULL,
  `doc_id` bigint(20) DEFAULT NULL,
  `tid` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `patient`
--

INSERT INTO `patient` (`pid`, `padd`, `pdob`, `pmobile`, `pname`, `doc_id`, `tid`) VALUES
(601, 'Mumbai', '2022-03-11', 8457852569, 'Rakesh update', 201, 501),
(602, 'Chennai', '2022-03-05', 9856987412, 'Ramesh', 201, 502),
(123452, 'Delhi', '2022-03-12', 7452365894, 'Bipin', 202, 501),
(123453, 'Delhi', '2022-03-11', 7856985658, 'nayan', 204, 502),
(123454, 'Delhi', '2022-03-12', 785236478, 'Nidhi', 202, 502),
(123455, 'kolkata', '2022-03-08', 7896441256, 'hello update', 202, 502),
(123456, 'mumbai', '2022-03-10', 7854236589, 'Anup', 203, 503);

-- --------------------------------------------------------

--
-- Table structure for table `roles`
--

CREATE TABLE `roles` (
  `id` bigint(20) NOT NULL,
  `name` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `roles`
--

INSERT INTO `roles` (`id`, `name`) VALUES
(1, 'ROLE_USER'),
(2, 'ROLE_ADMIN');

-- --------------------------------------------------------

--
-- Table structure for table `specialization`
--

CREATE TABLE `specialization` (
  `spec_id` bigint(20) NOT NULL,
  `speciality` varchar(255) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `specialization`
--

INSERT INTO `specialization` (`spec_id`, `speciality`) VALUES
(401, 'Surgeon'),
(402, 'Neurologist'),
(403, 'Orthopedics'),
(404, 'Obstetrics and Gynecology'),
(405, 'Dermatology'),
(406, 'Pediatrics'),
(407, 'Radiology'),
(408, 'General Surgery'),
(409, 'Anesthesia'),
(410, 'Pathology');

-- --------------------------------------------------------

--
-- Table structure for table `test`
--

CREATE TABLE `test` (
  `tid` bigint(20) NOT NULL,
  `t_date` date DEFAULT NULL,
  `t_name` varchar(255) DEFAULT NULL,
  `doc_id` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `test`
--

INSERT INTO `test` (`tid`, `t_date`, `t_name`, `doc_id`) VALUES
(501, '2022-03-01', 'Antithyroid Microsomal Antibody', 202),
(502, '2022-03-10', 'Activated Partial Thromboplastin Time', 202),
(503, '2022-03-10', 'Blood Test', 205),
(504, '2022-03-04', 'Dr. Ankur Yadav', 204);

-- --------------------------------------------------------

--
-- Table structure for table `users`
--

CREATE TABLE `users` (
  `id` bigint(20) NOT NULL,
  `password` varchar(120) DEFAULT NULL,
  `username` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `users`
--

INSERT INTO `users` (`id`, `password`, `username`) VALUES
(1, '$2a$10$5pzS6lsBQyMQrzHZpkJSB.R5ACUZhALlGSkM4qixpEWyuSijj3AQ6', 'Ram'),
(2, '$2a$10$iHDo0/XCnk9CRsSomLcbguxx4EDUyko9HO7TS8bXTITtrvALp1ANO', 'Akash'),
(3, '$2a$10$axBx2k3pb22pr1rnqZOPqOl6wYiSrtyFODO0fwjqMPcGXC3Vduhue', 'Dinesh'),
(4, '$2a$10$Gsfz6JZXcd9WuO8W6GW.4.fmdwPXKoqmx6cX9VeUcl2K3W2qu4GAG', 'Nishi'),
(5, '$2a$10$3FTJivfDswsbc3qGLyvehu/0qyal6JomqsA.Kkewh.oyOjhe8q8PS', 'Sintu'),
(6, '$2a$10$mwdS0Fuz5hn5iKlNKD4Ukea5mmJZhcb84JklgiRG36UNsvB1IBC8C', 'Bhabna'),
(7, '$2a$10$ZzzirqjwxKXGQ2H0HY3fQe6hY66YVgE4KPvxovOY2hMIZKxoQisEO', 'Anup');

-- --------------------------------------------------------

--
-- Table structure for table `user_roles`
--

CREATE TABLE `user_roles` (
  `user_id` bigint(20) NOT NULL,
  `role_id` bigint(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `user_roles`
--

INSERT INTO `user_roles` (`user_id`, `role_id`) VALUES
(1, 2),
(2, 1),
(4, 1),
(5, 1),
(6, 1),
(7, 1);

-- --------------------------------------------------------

--
-- Table structure for table `ward`
--

CREATE TABLE `ward` (
  `ward_id` bigint(20) NOT NULL,
  `ward_name` varchar(255) DEFAULT NULL,
  `doc_id` bigint(20) DEFAULT NULL,
  `pid` bigint(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data for table `ward`
--

INSERT INTO `ward` (`ward_id`, `ward_name`, `doc_id`, `pid`) VALUES
(1, 'Rohit', 201, 601),
(2, 'Ram', 203, 123452),
(3, 'Stuti', 202, 123454),
(4, 'Ankur', 204, 123453);

--
-- Indexes for dumped tables
--

--
-- Indexes for table `bill`
--
ALTER TABLE `bill`
  ADD PRIMARY KEY (`bill_id`),
  ADD KEY `FKfw5v8t5bkjx72ac7h58qi0562` (`ins_no`),
  ADD KEY `FKh941f5058tlqw6j1c7qp8mx74` (`pid`);

--
-- Indexes for table `department`
--
ALTER TABLE `department`
  ADD PRIMARY KEY (`dep_id`);

--
-- Indexes for table `doctor`
--
ALTER TABLE `doctor`
  ADD PRIMARY KEY (`doc_id`),
  ADD KEY `FKrhv4q8knqp7ndoay0bpan90m` (`dep_id`),
  ADD KEY `FKhtg9fc5khxff61vpvfik5mnan` (`spec_id`);

--
-- Indexes for table `employee`
--
ALTER TABLE `employee`
  ADD PRIMARY KEY (`emp_id`),
  ADD KEY `FKe18129hcd0klevt866ww22wnd` (`dep_id`);

--
-- Indexes for table `insurance`
--
ALTER TABLE `insurance`
  ADD PRIMARY KEY (`ins_no`),
  ADD KEY `FKhu7ltl1axq4u6mv7qm14qdfw8` (`pid`);

--
-- Indexes for table `medicos`
--
ALTER TABLE `medicos`
  ADD PRIMARY KEY (`med_id`),
  ADD KEY `FKi4rlra7tnv63w9lritkcbst25` (`doc_id`),
  ADD KEY `FKeuaf9d23nnt02t4b9jipq68ad` (`pid`);

--
-- Indexes for table `operation`
--
ALTER TABLE `operation`
  ADD PRIMARY KEY (`op_id`),
  ADD KEY `FKpmmteo1g1ttko3auyf6tqsbep` (`doc_id`),
  ADD KEY `FKs2gk0divwbpw48xdkfe2mvpv2` (`pid`);

--
-- Indexes for table `patient`
--
ALTER TABLE `patient`
  ADD PRIMARY KEY (`pid`),
  ADD KEY `FKcsxkcj2mvv8ddtcwhvsreoeun` (`doc_id`),
  ADD KEY `FKlp6gs42tikikelrwem03x4fb4` (`tid`);

--
-- Indexes for table `roles`
--
ALTER TABLE `roles`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `specialization`
--
ALTER TABLE `specialization`
  ADD PRIMARY KEY (`spec_id`);

--
-- Indexes for table `test`
--
ALTER TABLE `test`
  ADD PRIMARY KEY (`tid`),
  ADD KEY `FK7isfaa9rtcgl34q2jj33tpw6e` (`doc_id`);

--
-- Indexes for table `users`
--
ALTER TABLE `users`
  ADD PRIMARY KEY (`id`),
  ADD UNIQUE KEY `UKr43af9ap4edm43mmtq01oddj6` (`username`);

--
-- Indexes for table `user_roles`
--
ALTER TABLE `user_roles`
  ADD PRIMARY KEY (`user_id`,`role_id`),
  ADD KEY `FKh8ciramu9cc9q3qcqiv4ue8a6` (`role_id`);

--
-- Indexes for table `ward`
--
ALTER TABLE `ward`
  ADD PRIMARY KEY (`ward_id`),
  ADD KEY `FKfxn9u86ho096cimss2ofx8u1p` (`doc_id`),
  ADD KEY `FKdm0f59ji09ho6p4flq7afmdmh` (`pid`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `bill`
--
ALTER TABLE `bill`
  MODIFY `bill_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=123455;

--
-- AUTO_INCREMENT for table `department`
--
ALTER TABLE `department`
  MODIFY `dep_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=109;

--
-- AUTO_INCREMENT for table `doctor`
--
ALTER TABLE `doctor`
  MODIFY `doc_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=206;

--
-- AUTO_INCREMENT for table `employee`
--
ALTER TABLE `employee`
  MODIFY `emp_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=105;

--
-- AUTO_INCREMENT for table `insurance`
--
ALTER TABLE `insurance`
  MODIFY `ins_no` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=1234504;

--
-- AUTO_INCREMENT for table `medicos`
--
ALTER TABLE `medicos`
  MODIFY `med_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

--
-- AUTO_INCREMENT for table `operation`
--
ALTER TABLE `operation`
  MODIFY `op_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=303;

--
-- AUTO_INCREMENT for table `patient`
--
ALTER TABLE `patient`
  MODIFY `pid` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=123457;

--
-- AUTO_INCREMENT for table `roles`
--
ALTER TABLE `roles`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=703;

--
-- AUTO_INCREMENT for table `specialization`
--
ALTER TABLE `specialization`
  MODIFY `spec_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=411;

--
-- AUTO_INCREMENT for table `test`
--
ALTER TABLE `test`
  MODIFY `tid` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=505;

--
-- AUTO_INCREMENT for table `users`
--
ALTER TABLE `users`
  MODIFY `id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=8;

--
-- AUTO_INCREMENT for table `ward`
--
ALTER TABLE `ward`
  MODIFY `ward_id` bigint(20) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- Constraints for dumped tables
--

--
-- Constraints for table `bill`
--
ALTER TABLE `bill`
  ADD CONSTRAINT `FKfw5v8t5bkjx72ac7h58qi0562` FOREIGN KEY (`ins_no`) REFERENCES `insurance` (`ins_no`),
  ADD CONSTRAINT `FKh941f5058tlqw6j1c7qp8mx74` FOREIGN KEY (`pid`) REFERENCES `patient` (`pid`);

--
-- Constraints for table `doctor`
--
ALTER TABLE `doctor`
  ADD CONSTRAINT `FKhtg9fc5khxff61vpvfik5mnan` FOREIGN KEY (`spec_id`) REFERENCES `specialization` (`spec_id`),
  ADD CONSTRAINT `FKrhv4q8knqp7ndoay0bpan90m` FOREIGN KEY (`dep_id`) REFERENCES `department` (`dep_id`);

--
-- Constraints for table `employee`
--
ALTER TABLE `employee`
  ADD CONSTRAINT `FKe18129hcd0klevt866ww22wnd` FOREIGN KEY (`dep_id`) REFERENCES `department` (`dep_id`);

--
-- Constraints for table `insurance`
--
ALTER TABLE `insurance`
  ADD CONSTRAINT `FKhu7ltl1axq4u6mv7qm14qdfw8` FOREIGN KEY (`pid`) REFERENCES `patient` (`pid`);

--
-- Constraints for table `medicos`
--
ALTER TABLE `medicos`
  ADD CONSTRAINT `FKeuaf9d23nnt02t4b9jipq68ad` FOREIGN KEY (`pid`) REFERENCES `patient` (`pid`),
  ADD CONSTRAINT `FKi4rlra7tnv63w9lritkcbst25` FOREIGN KEY (`doc_id`) REFERENCES `doctor` (`doc_id`);

--
-- Constraints for table `operation`
--
ALTER TABLE `operation`
  ADD CONSTRAINT `FKpmmteo1g1ttko3auyf6tqsbep` FOREIGN KEY (`doc_id`) REFERENCES `doctor` (`doc_id`),
  ADD CONSTRAINT `FKs2gk0divwbpw48xdkfe2mvpv2` FOREIGN KEY (`pid`) REFERENCES `patient` (`pid`);

--
-- Constraints for table `patient`
--
ALTER TABLE `patient`
  ADD CONSTRAINT `FKcsxkcj2mvv8ddtcwhvsreoeun` FOREIGN KEY (`doc_id`) REFERENCES `doctor` (`doc_id`),
  ADD CONSTRAINT `FKlp6gs42tikikelrwem03x4fb4` FOREIGN KEY (`tid`) REFERENCES `test` (`tid`);

--
-- Constraints for table `test`
--
ALTER TABLE `test`
  ADD CONSTRAINT `FK7isfaa9rtcgl34q2jj33tpw6e` FOREIGN KEY (`doc_id`) REFERENCES `doctor` (`doc_id`);

--
-- Constraints for table `user_roles`
--
ALTER TABLE `user_roles`
  ADD CONSTRAINT `FKh8ciramu9cc9q3qcqiv4ue8a6` FOREIGN KEY (`role_id`) REFERENCES `roles` (`id`),
  ADD CONSTRAINT `FKhfh9dx7w3ubf1co1vdev94g3f` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`);

--
-- Constraints for table `ward`
--
ALTER TABLE `ward`
  ADD CONSTRAINT `FKdm0f59ji09ho6p4flq7afmdmh` FOREIGN KEY (`pid`) REFERENCES `patient` (`pid`),
  ADD CONSTRAINT `FKfxn9u86ho096cimss2ofx8u1p` FOREIGN KEY (`doc_id`) REFERENCES `doctor` (`doc_id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
