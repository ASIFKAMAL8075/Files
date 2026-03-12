https://www.onlinegdb.com/0m5S-FOsJj


https://drive.google.com/drive/folders/19W3X8s5tWeRiM5mxVW6qGNP_SiTiaw5i?usp=sharing




[11/03, 9:21 pm] Shahad Ssm: 1. Create college database and make an table with id,name,department,marks and insert two data's to the table
2. Make an login page with  session and cookie. when user login save it into session and print welcome back then set an logout button when click that the session will clear and show the login page.
3. praveenode chodikendi varum. avank ariyam.
[11/03, 10:31 pm] Shahad Ssm: 3. create cookie for store username
cookie expire time = 1 day
display username form cookie


wp 1


<?php

$servername = "localhost";
$username = "root";
$password = "";

// Connect to MySQL
$conn = new mysqli($servername, $username, $password);

if ($conn->connect_error) {
die("Connection failed: " . $conn->connect_error);
}

// Create database
$conn->query("CREATE DATABASE IF NOT EXISTS college");

// Select database
$conn->select_db("college");

// Create table
$conn->query("CREATE TABLE IF NOT EXISTS students(
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(100),
department VARCHAR(100),
marks INT
)");

if ($_SERVER['REQUEST_METHOD'] == 'POST') {

$name = $_POST['name'];
$department = $_POST['department'];
$marks = $_POST['marks'];

$conn->query("INSERT INTO students(name,department,marks)
VALUES('$name','$department','$marks')");

echo "Data inserted successfully<br>";
}

// Display table
$result = $conn->query("SELECT * FROM students");

echo "<h2>Students Table</h2>";
echo "<table border='1'>
<tr>
<th>ID</th>
<th>Name</th>
<th>Department</th>
<th>Marks</th>
</tr>";

while($row = $result->fetch_assoc()){
echo "<tr>
<td>".$row['id']."</td>
<td>".$row['name']."</td>
<td>".$row['department']."</td>
<td>".$row['marks']."</td>
</tr>";
}

echo "</table>";

$conn->close();

?>

<!DOCTYPE html>
<html>
<body>

<h2>Insert Student</h2>

<form method="POST">

<input type="text" name="name" placeholder="Name" required><br><br>

<input type="text" name="department" placeholder="Department" required><br><br>

<input type="number" name="marks" placeholder="Marks" required><br><br>

<button type="submit">Insert</button>

</form>

</body>
</html>


wp2



<?php
session_start();

if ($_SERVER['REQUEST_METHOD'] == 'POST') {

if(isset($_POST['login'])){

$username = $_POST['username'];

$_SESSION['username'] = $username;

// cookie expires in 1 hour
setcookie("username",$username,time()+3600);

}

if(isset($_POST['logout'])){
session_destroy();
header("Location: login.php");
}

}
?>

<!DOCTYPE html>
<html>
<head>
<title>Login Page</title>
</head>
<body>

<?php

if(isset($_SESSION['username'])){

echo "<h2>Welcome back ".$_SESSION['username']."</h2>";

?>

<form method="POST">
<button name="logout">Logout</button>
</form>

<?php
}
else{
?>

<h2>Login</h2>

<form method="POST">
<input type="text" name="username" placeholder="Enter Username" required>
<button type="submit" name="login">Login</button>
</form>

<?php
}
?>

</body>
</html>



wp3


<?php

if ($_SERVER['REQUEST_METHOD'] == 'POST') {

$username = $_POST['username'];

// cookie expires in 1 day
setcookie("username",$username,time()+86400);

echo "Cookie created successfully<br>";

}

if(isset($_COOKIE['username'])){
echo "Username from Cookie: ".$_COOKIE['username'];
}

?>

<!DOCTYPE html>
<html>
<head>
<title>Cookie Example</title>
</head>
<body>

<form method="POST">

<label>Enter Username</label><br>

<input type="text" name="username" required><br><br>

<button type="submit">Submit</button>

</form>

</body>
</html>




