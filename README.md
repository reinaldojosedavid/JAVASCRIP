# JAVASCRIP
<!DOCTYPE html>
<html lang="es">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link rel="stylesheet" href="styles.css">
  <title>Notas de tarjetas</title>
</head>
<body>

	<div class="container">
		<div class="title">
		 Cantidad de Notas
		</div>

		<label>Ingresa la cantidad de tarjetas </label>
		<input type="number" name="tarjetas" id="tarjetas">
		<button type="button" onclick="generador();">Generar</button>
		<div id="contenido"></div>


		<div id="resultado"></div>

	
	<script type="text/javascript">
		function generador(){
			let tarjetas = document.getElementById('tarjetas').value;
			let contenido = document.getElementById('contenido');
			let resultado = document.getElementById('resultado');
			var contenedor = '';
			for (var i = 0; i < tarjetas; i++) {
				contenedor += '<label>Ingresa nombre del alumno '+(i+1)+'</label>';
				contenedor += '<input type="text" name="nombre[]" class="nombre"> <br>';
				contenedor += '<label>Ingresa nota de matematicas </label>';
				contenedor += '<input type="number" name="nota_matematica[]" class="nota_matematica"> <br>';
				contenedor += '<label>Ingresa nota de fisica </label>';
				contenedor += '<input type="number" name="nota_fisica[]" class="nota_fisica"> <br>';
				contenedor += '<label>Ingresa nota de programacion </label>';
				contenedor += '<input type="number" name="nota_programacion[]" class="nota_programacion"> <br>';
			};
			contenedor += '<button onclick="calcular();">Calcular</button>';
			contenido.innerHTML = contenedor;
		}


		function calcular() {
			//nota promedio de cada materia
			let tarjetas = document.getElementById('tarjetas').value;
			let mate = document.getElementsByName('nota_matematica[]');
			let fisica = document.getElementsByName('nota_fisica[]');
			let programacion = document.getElementsByName('nota_programacion[]');
			
			sum_mate = 0;
			sum_fisica = 0;
			sum_progra = 0;

			apro_mate = 0; 
			repro_mate = 0; 
			apro_fisica = 0; 
			repro_fisica = 0; 
			apro_progra = 0;
			repro_progra = 0;

			alu_todas_materias = 0;
			alu_dos_materias = 0;
			alu_una_materia = 0;

			mayor_mate = 0;
			mayor_fisica = 0;
			mayor_progra = 0;
			for (let j = 0; j < mate.length; j++) {
				
				sum_mate += parseInt(mate[j].value);		
				sum_fisica += parseInt(fisica[j].value);
				sum_progra += parseInt(programacion[j].value);	

				if (mate[j].value >= 10) {
					apro_mate++;
				} else {
					repro_mate++;
				}
				if (fisica[j].value >= 10) {
					apro_fisica++;
				} else {
					repro_fisica++;
				}
				if (programacion[j].value >= 10) {
					apro_progra++;
				} else {
					repro_progra++;
				}


				if (mate[j].value >= 10 && fisica[j].value >= 10 && programacion[j].value >= 10) {
					alu_todas_materias++;
				}

				if (mate[j].value >= 10 || fisica[j].value >= 10 || programacion[j].value >= 10) {
					alu_una_materia++;
				}


				if ((mate[j].value >= 10 && fisica[j].value >= 10) || 
				    (fisica[j].value >= 10 && programacion[j].value >= 10 ) ||
					(mate[j].value >= 10 && programacion[j].value >= 10 )
					) {
					alu_dos_materias++;
				}
				
				if (mate[j].value > mayor_mate){
					mayor_mate = mate[j].value;
				}

				if (fisica[j].value > mayor_fisica){
					mayor_mate = fisica[j].value;
				}

				if (programacion[j].value > mayor_progra){
					mayor_progra = programacion[j].value;
				}
			}

			
			resultado.innerHTML += 'Promedio de notas mate: '+ (sum_mate/tarjetas)+'<br>'; 
			resultado.innerHTML +='Promedio de notas fisica: '+ (sum_fisica/tarjetas)+'<br>';  
			resultado.innerHTML +='Promedio de notas programacion: '+ (sum_progra/tarjetas)+'<br>'; 

			resultado.innerHTML +='Alumnos aprobado en mate: '+apro_mate+'<br>'; 
			resultado.innerHTML +='Alumnos reprobado en mate: '+repro_mate+'<br>'; 

			resultado.innerHTML +='Alumnos aprobado en fisica: '+apro_fisica+'<br>'; 
			resultado.innerHTML +='Alumnos reprobado en fisica: '+repro_fisica+'<br>'; 

			resultado.innerHTML +='Alumnos aprobado en programacion: '+apro_progra+'<br>'; 
			resultado.innerHTML +='Alumnos reprobado en programacion: '+repro_progra+'<br>'; 

			
			resultado.innerHTML +='Alumnos aprobado todas las materias: '+alu_todas_materias+'<br>'; 
			resultado.innerHTML +='Alumnos aprobado dos materias: '+alu_dos_materias+'<br>'; 
			resultado.innerHTML +='Alumnos aprobado una materia: '+alu_una_materia+'<br>'; 

			resultado.innerHTML +='La nota mayor de mate: '+mayor_mate+'<br>'; 
			resultado.innerHTML +='La nota mayor de fisica: '+mayor_fisica+'<br>'; 
			resultado.innerHTML +='La nota mayor de programacion: '+mayor_progra+'<br>'; 

		}
	</script>
</body>
</html>
