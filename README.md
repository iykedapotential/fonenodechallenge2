fonenodechallenge2
==================
<?php 
class stud
{
    var $rate;
    var $candy;
}

if(isset($_POST['send']))
{
    $ratings = trim($_POST['ratings']);
    $nos = explode(' ',$ratings);
    $std = array();
    $candies = 0;
    $no = count($nos); 
    
    foreach($nos as $n)
    {
        $std[] = new stud();
    }
    
    foreach($nos as $n => $v)
    {
        $std[$n]->rate = (int)$v;
        $std[$n]->candy = 1;
    }
    
   foreach($nos as $i=>$k)
    { 
        if(($i+1) == $no)
        break;
        
        if(((int)$std[$i]->rate > (int)$std[$i+1]->rate))
        {
            $std[$i]->candy += 1;
            
        }
        elseif((int)$std[$i]->rate < (int)$std[$i+1]->rate)
        {
            $std[$i+1]->candy += 1;
            
        }
        
    }
    
    foreach($nos as $n => $v)
    {
        
        $candies += $std[$n]->candy;
    }
    
    
    
}
?>
<!DOCTYPE HTML>
<html>
<head>
	<meta http-equiv="content-type" content="text/html" />
	<meta name="author" content="ODUMGBO" />

	<title>Fonenode Challenge 2</title>
</head>

<body>
<div align="center" style="margin-top: 100px;">
<p>Enter the array of ratings</p><span>Format: A number followed by a space</span>
<form method="post" action="">
<textarea name="ratings"></textarea><br />
<input type="submit" name="send" value="Submit" />
</form>
<p>&nbsp;</p>
<p>&nbsp;</p>
<?php if(isset($candies))
{
    echo '<p>Ratings:    ['.$ratings.']</p>';
    echo '<p>Answer:  '.$candies.'</p>';
} ?>
</div>

</body>
</html>
