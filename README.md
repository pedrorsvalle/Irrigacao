########################### Projeto de Irrigacao - Usando a Internet########################### 
###############################################################################################



Banco de Dados:

<?php


$dbHost ='localhost';
$dbUsername ='root';
$dbPassaword ='';
$dbName ='projeto';

$conexao = new mysqli($dbHost,$dbUsername,$dbPassaword,$dbName);

    if($conexao->connect_errno){

        echo"Erro";
}

else{
    echo"Conexão efetuada com sucesso";
}


?>
_____________________________________________________________________________________________

CadastroSensor:

<?php


if(isset($_GET['submit']))
{
    
    

include_once('banco.php');


$descricao =$_GET['descricao'];
$localizacao=$_GET['localizacao'];
$data       =  $_GET['data'];
$umidade    =  $_GET['umidade'];
$usuario_idusuario = $_GET['idusuario'];


//$result =mysqli_query($conexao ,"INSERT INTO sensor('data',umidade,usuario_idusuario)VALUES
//('$data','$umidade','$usuario_idusuario')");

//$result =mysqli_query($conexao ,"INSERT INTO sensor('data',umidade,usuario_idusuario)VALUES
//('$data','$umidade',1)");

// INSERT INTO sensor(data,descricao,localizacao,umidade,usuario_idusuario)VALUES ('2022-04-28','fazenda','sp','molhado',3)

$Sql ="INSERT INTO sensor(data,descricao,localizacao,umidade,usuario_idusuario)VALUES
('$data','$descricao','$localizacao','$umidade',$usuario_idusuario)";
//echo $Sql;
$result =mysqli_query($conexao ,$Sql );

}

?>
_____________________________________________________________________________________________

Cadastro Usuario:


<?php


if(isset($_GET['submit']))
{
    
    

include_once('banco.php');

$nome      =  $_GET['nome'];
$email       =  $_GET['email'];
$telefone =  $_GET['telefone'];

$result =mysqli_query($conexao ,"INSERT INTO usuario(nome,email,telefone)VALUES
('$nome','$email','$telefone')");


}

?>
_____________________________________________________________________________________________


Sensor.Php




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>sensor </title>
    <style>


    </style>
</head>
<body>


    <div class="box">
        <form action="cadastrosensor.php" method = "GET">
            <fieldset>
                <legend><b>Sensor </b></legend>
                <br>
                <div class="inputBox">
                    <input type="date" name="data" id="data" class="inputUser" required>
                    <label for="data" class="labelInput">data </label>
                </div>
                <br><br>

                  <div class="inputBox">
                   <input type="descricao" name="descricao" id="descricao" class="inputUser" required>
                    <label for="descricao" class="labelInput">descricao </label>
                </div>
                <br><br>

                <div class="inputBox">
                    <input type="localizacao" name="localizacao" id="localizacao" class="inputUser" required>
                    <label for="localizacao" class="labelInput">localizacao </label>
                </div>
                <br><br>


                <p>Umidade:</p>
                <input type="radio" id="umidade" name="umidade" value="seco" required>
                <label for="umidade">seco</label>
                <br>
                <input type="radio" id="umidade" name="umidade" value="molhado" required>
                <label for="umidade">molhado</label>
                <br>
                <input type="radio" id="umidade" name="umidade" value="umido" required>
                <label for="umidade">umido</label>
                <br><br><br>

                <input type="text" id="usuario_idusuario" name="idusuario" value="" required>
                <label for="idusuario">usuario</label> 
                <br><br>


                <input type="button" value="Voltar" onClick="history.go(-2)"> 


              
               
<html>
<body>
<form>
    <a href="cadastrosensor.php">
        

        <input type="submit" name="submit" id="submit">  <br> <br>

    </a>
</form>
</body>

    <form>

    <input type="button" value="Avançar" onCLick="history.forward()">

   




</form>

</html>
               
               

            </fieldset>
        </form>
    </div>


 
</body>
</html>

_____________________________________________________________________________________________
Usuario.php


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro Usuario </title>
    <style>


    </style>
</head>
<body>


    <div class="box">
        <form action="cadastrousuario.php" method = "get">
            <fieldset>
                <legend><b>Usuario </b></legend>
                <br>
                <div class="inputBox">
                    <input type="text" name="nome" id="nome" class="inputUser" required>
                    <label for="nome" class="labelInput">nome</label>
                </div>
                <br><br>
                <div class="inputBox">
                    <input type="text" name="email" id="email" class="inputUser" required>
                    <label for="email" class="labelInput">email</label>
                </div>
                <br><br>

                <div class="inputBox">
                    <input type="text" name="telefone" id="telefone" class="inputUser" required>
                    <label for="telefone" class="labelInput">telefone</label>
                </div>
                <br><br>

               


                
                <input type="submit" name="submit" id="submit"> <br>

                
            </fieldset>
        </form>
        <form>


    
</form>


    </div>
</body>
</html>

_____________________________________________________________________________________________
