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

5. __Configure PHP Files__
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

## Code Explanation

### PHP Code
```
// Connect to MySQL
$servername = "localhost";
$username = "root"; // Default username
$password = ""; // Default password, if any
$dbname = "robot_control"; // Your database name
```
These variables store the MySQL server details (server name, username, password, database name).
```
// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);
```
Creates a new MySQLi object $conn to establish a connection to the MySQL database using the provided credentials.

```
// Check connection
if ($conn->connect_error) {
    // If connection fails, output an error message and terminate script
    die("Connection failed: " . $conn->connect_error);
}
```
Checks if the connection to the MySQL database is successful. If not, it terminates the script and displays an error message.

```
// Process form submission when the HTTP method is POST
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $direction = $_POST["direction"]; // Retrieve direction value from POST data
```
Checks if the HTTP request method is POST, indicating that form data has been submitted. Retrieves the value of direction from the POST data.

```
    // Insert into database
    $sql = "INSERT INTO directions (direction) VALUES ('$direction')";
```
Constructs an SQL query to insert the received direction value into the directions table of the robot_control database.

```
    // Execute SQL query and check if successful
    if ($conn->query($sql) === TRUE) {
        // If insertion is successful, output success message
        echo "Direction recorded successfully.";
    } else {
        // If there is an error with the SQL query, output error message
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
}
```
Executes the SQL query using $conn->query($sql). If successful, it outputs a success message. If there is an error, it outputs the SQL query and the specific error message.

```
// Close connection to MySQL
$conn->close();
```
Closes the connection to the MySQL database after completing the database operations.

### Index Code
```
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- Meta tags for character set and responsive design -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Robot Control</title>
```
Meta tags for character set and responsive design, and setting the page title.

```
    <!-- Internal CSS for styling the page and buttons -->
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .button-container {
            display: grid;
            grid-template-areas:
                ". up ."
                "left stop right"
                ". down .";
            gap: 10px;
        }
        button {
            width: 80px;
            height: 80px;
            background-color: #FFFFFF;
            color: #000000;
            border: 2px solid transparent;
            border-radius: 50%;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        button:active {
            border-color: #FF0000;
        }
        button.stop {
            grid-area: stop;
            background-color: #FF0000;
            color: #FFFFFF;
        }
        button.up {
            grid-area: up;
        }
        button.down {
            grid-area: down;
        }
        button.left {
            grid-area: left;
        }
        button.right {
            grid-area: right;
        }
    </style>
```
Defines the styles for the webpage, making the buttons centered and styled as desired.

```
    <!-- Internal JavaScript for handling button clicks -->
    <script>
        function recordDirection(direction) {
            var xhr = new XMLHttpRequest();
            xhr.open("POST", "record.php", true);
            xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
            xhr.onreadystatechange = function() {
                if (xhr.readyState === XMLHttpRequest.DONE) {
                    if (xhr.status === 200) {
                        console.log("Direction recorded successfully.");
                    } else {
                        console.error("Error recording direction.");
                    }
                }
            };
            xhr.send("direction=" + direction);
        }
```
JavaScript to handle button clicks and send AJAX requests

```
    </script>
</head>
<body>
    <!-- Container for directional buttons -->
    <div class="button-container">
        <!-- Buttons for robot control -->
        <button type="button" onclick="recordDirection('forward')" class="up">Forward</button>
        <button type="button" onclick="recordDirection('backward')" class="down">Backward</button>
        <button type="button" onclick="recordDirection('left')" class="left">Left</button>
        <button type="button" onclick="recordDirection('right')" class="right">Right</button>
        <button type="button" onclick="recordDirection('stop')" class="stop">Stop</button>
    </div>
</body>
</html>
```
Creates a container for directional buttons and defines each button with an onclick event to record the direction.
