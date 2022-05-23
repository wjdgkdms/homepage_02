# homepage_02
//로그인 DB설계
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

<?php
    
     if(isset($_POST['id'])&&isset($_POST['pw'])){
      $id2=$_POST['id'];
      $pw2=$_POST['pw'];
     
      $conn=mysqli_connect('localhost','root','050407','silver','3307');
      
      $sql="SELECT * FROM log where id='$id2'&& pw='$pw2'";
      if($result=mysqli_fetch_array(mysqli_query($conn,$sql))){
        echo "사용자 이름= $id2";
        echo "</br>".$result['created'];
      }
        $row = mysqli_fetch_array(mysqli_query($conn,$sql));
        if ($row != null) {
            $_SESSION['id'] = $row['id'];
            session_start();
            echo"<script> alert('로그인 되었습니다.'); 
            location.href='./loginindex.php'; </script>";
      }
      else{
        echo"<script> alert('로그인 실패하였습니다. 다시 확인해주세요.'); location.href='./index.php'; </script>";
      }
    }
  
 ?>
</body>

</html>
