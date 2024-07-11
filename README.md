# Web Task 1

## Description
This task includes designing a web interface to control a robot's leg movements using directional buttons. The actions performed by the user on the webpage are recorded in a 
MySQL database using PHP scripts. The task demonstrates the integration of HTML, CSS, PHP, and MySQL, hosted locally using XAMPP. 

## Features
- __Web Interface:__ A user-friendly webpage with buttons to control the robot's movements.
- __Database Integration:__ Actions are stored in a MySQL database, providing a history of movements.
- __PHP Backend:__ PHP scripts handle database interactions.
- __Local Hosting:__ Uses XAMPP to host the webpage and manage the database locally.

## Installation

### Prerequisites 
- XAMPP (includes Apache server and MySQL database)
- Visual Studio Code or any other code editor
- Web browser (e.g., Chrome, Firefox)

### Steps
1. __Download the project folder "RobotControl" from the repository.__
2. __Setup XAMPP__
- Download and install XAMPP from the [official website](https://www.apachefriends.org/download.html).
- Start the XAMPP Control Panel and ensure both Apache and MySQL are running.

  <img width="498" alt="image" src="https://github.com/Alaa3172/WebTask1/assets/173661540/6ce74776-3b03-4911-877a-6f4a0b9a5aa9">

3. __Move Project Files__
- Copy the downloaded project folder __"Robot Control"__ to the htdocs directory in your XAMPP installation. The default path is C:\xampp\htdocs\ on Windows or
/Applications/XAMPP/htdocs/ on macOS.

  <img width="959" alt="image" src="https://github.com/Alaa3172/WebTask1/assets/173661540/dd6b8311-7225-42af-940c-3d0753c6de88">

4. __Create the Database__
- Open your web browser and go to http://localhost/phpmyadmin.

  <img width="959" alt="image" src="https://github.com/Alaa3172/WebTask1/assets/173661540/0a88d89f-7b6f-469e-ad0a-0ca958e8084c">

- Create a new database named __'robot_control'__.

  <img width="944" alt="image" src="https://github.com/Alaa3172/WebTask1/assets/173661540/eb73e4b8-598e-4af8-b8b9-e0a27558a34b">

- Create a table named __'directions'__ with the following structure:
  - id (INT, 11)
  - direction (VARCHAR, 50)

  <img width="777" alt="image" src="https://github.com/Alaa3172/WebTask1/assets/173661540/d00058f4-9a60-493b-9c2a-5edf0c6fa9f5">

5. Configure PHP Files
- Open __'record.php'__ in your code editor.
- Ensure the database connection details (host, username, password, database name) are correct:

  <img width="367" alt="image" src="https://github.com/Alaa3172/WebTask1/assets/173661540/08da3848-bc1f-45d5-8257-725ac2a2ff57">

## Usage
1. __Start the Server__
- Open the XAMPP Control Panel and ensure Apache and MySQL are running.
2. __Access the Webpage__
- Open your web browser and navigate to http://localhost/RobotControl/index.php.
- You should see a webpage with directional buttons (Left, Right, Forward, Backward, Stop).
3. __Control the Robot__
- Click the buttons to simulate moving the robot's legs.
- Each button click records the action in the __'directions'__ table in the __'robot_control'__ database.

## File Structure
- __index.php__ - Contains HTML, CSS, and JavaScript for the webpage.
- __record.php__ - PHP script that saves button actions to the database.

## Screenshots

  <img width="959" alt="image" src="https://github.com/user-attachments/assets/7d2e5c80-6f3d-4ce1-a1c4-cae9c0e761ab">

Figure 1: Main interface with directional buttons.

  <img width="949" alt="image" src="https://github.com/user-attachments/assets/eb37b335-5ca7-4dfc-9018-23510e1821f2">

Figure 2: Database table structure and recorded actions.

## Code









































   



