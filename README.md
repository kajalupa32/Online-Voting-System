Online Voting System

A desktop voting application built with Java Swing (AWT) for the front end and MySQL via JDBC for the back end. Registered voters log in, view candidate profiles, cast exactly one vote, and receive a digital receipt.

Features
Voter login: Voter ID and password (passwords are stored as SHA-256 hashes)
One vote per voter: enforced by a UNIQUE database constraint, a row lock and a transaction
Candidate list: interactive profile cards with avatar, party, age and manifesto
Search and filter bar: search by name or party, filter by party
Live voter turnout bar: updates every 3 seconds from the database
Smart UI disabling: buttons and cards are enabled or disabled depending on the voter's state
Confirmation dialog: "Are you sure?" pop-up before a vote is cast
Digital receipt: shown on screen and saved as a text file in the receipts/ folder
Results: candidate-wise vote counts shown as progress bars
Dynamic Help and Instructions dialog: highlights the voter's current step
Tech Stack
Layer	Technology
Front end	Java Swing / AWT
Back end	MySQL 8
Connectivity	JDBC (MySQL Connector/J)
Language	Java (JDK 11 or newer)
Project Structure
Online-Voting-System/
 ├─ src/
 │   ├─ Main.java              (program entry point)
 │   ├─ DBConnection.java      (JDBC connection)
 │   ├─ Voter.java             (voter data class)
 │   ├─ Candidate.java         (candidate data class)
 │   ├─ VotingDAO.java         (all SQL queries)
 │   ├─ LoginFrame.java        (login screen)
 │   ├─ VotingFrame.java       (main voting screen)
 │   ├─ CandidateCard.java     (interactive candidate card)
 │   ├─ ResultDialog.java      (results screen)
 │   ├─ HelpDialog.java        (dynamic help dialog)
 │   └─ ReceiptGenerator.java  (digital receipt)
 ├─ sql/
 │   └─ database.sql           (tables and sample data)
 ├─ lib/                       (put the MySQL Connector/J jar here)
 └─ README.md
How to Run
Install JDK 11+ and MySQL Server.
Open MySQL Workbench and run sql/database.sql. This creates the online_voting database, tables and sample data.
Download MySQL Connector/J from https://dev.mysql.com/downloads/connector/j/ and place the .jar file in the lib/ folder.
Open src/DBConnection.java and set your own MySQL username and password.
Compile and run from the project folder. Windows
   javac -cp "lib/*" -d out src/*.java
   java -cp "out;lib/*" Main

Linux / Mac

   javac -cp "lib/*" -d out src/*.java
   java -cp "out:lib/*" Main

In Eclipse: create a Java Project, copy the files into src, add the connector jar under Build Path → Configure Build Path → Libraries → Classpath → Add External JARs, then run Main.java.

Demo Login
Voter ID	Password
V001 to V040	pass123
Database Design
Table	Purpose
voters	voter ID, name, hashed password, has_voted flag
candidates	candidate ID, name, party, age, manifesto
votes	one row per vote; voter_id is UNIQUE so a voter can vote only once
Screenshots


Possible Future Improvements
Admin login to add or remove candidates and publish results when the election closes
Candidate photos instead of initials
Email or OTP verification for voters
Note on Development

This project was developed with the help of an AI assistant (Claude by Anthropic) for learning purposes.

Author
Kajal Upadhaya
