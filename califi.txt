<?php


$sentesql="select * from calificacion where lectivo='23-2' and nota1<9";




//Datos Coneccion
$ipservidor = "212.1.208.199";
$basedato = "u312507976_db";
$usuario = "u312507976_usuario1";
$clave = "Usuario23-2";

//Crear coneccion a DB
$coneccion = mysqli_connect($ipservidor, $usuario, $clave, $basedato);
if (!$coneccion) {die("Conección fallida" . mysqli_connect_error());} 

//CONSULTAR DB, actualize sentencia SQL
$sql= mysqli_query($coneccion,$sentesql);

//Titulo columna
echo "</p>";
$tabla='<table border=1>  <tr>
 <th> Lectivo </th> 
 <th> Cedula </th>
 <th> Codicarrera </th>
 <th> Codicurso </th>  
 <th> Codimateria </th> 
 <th> Nota1 </th> 
 <th> Nota2 </th>  
 <th> Fecharegistro </th>  </tr> ';


//Muestra datos de tabla
while ($fila = mysqli_fetch_assoc($sql)){
$tabla .= '<tr>
  <td>'.$fila['lectivo'].'</td>   
  <td>'.$fila['cedula'].'</td>
  <td>'.$fila['codicarrera'].'</td>
  <td>'.$fila['codicurso'].'</td>
  <td>'.$fila['codimateria'].'</td>  
  <td>'.$fila['nota1'].'</td>
  <td>'.$fila['nota2'].'</td>  
  <td>'.$fila['fecharegistro'].'</td>  
 </tr> '; }
$tabla .= '</table>';echo $tabla; 

//Cierra coneccion
mysqli_free_result($sql);mysqli_close($coneccion);

?>