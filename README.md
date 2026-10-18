# calculadora-android
This repository contains the work from the curse of movil compute

Ejercicio 1 en Android - Calculadora interactiva con formularios dinámicos
 

Desarrollar de manera individual una aplicación para Android utilizando Android Studio y Kotlin.

La aplicación deberá permitir al usuario seleccionar y resolver distintos tipos de cálculos mediante una interfaz dinámica. El objetivo principal del ejercicio es aplicar correctamente la interacción con componentes de interfaz, captura de datos, validación de formularios y procesamiento de la información ingresada por el usuario. 

1. Selección del cálculo

La aplicación deberá presentar un menú que contenga cuatro opciones de cálculo.

De estas cuatro opciones:


Al menos una deberá corresponder a una fórmula que requiera tres o más datos de entrada.
Las demás deberán requerir como mínimo dos datos.
No se podrán utilizar únicamente conversiones directas de unidades.
Cada opción deberá implicar algún tipo de procesamiento o validación particular.
Algunos ejemplos de cálculos posibles son:

Raíces reales de una ecuación de segundo grado.
Índice de masa corporal con clasificación del resultado.
Ley de Ohm.
Energía cinética.
Volumen y área de un cuerpo geométrico.
Interés simple o compuesto.
Conversión de temperatura con validación respecto al cero absoluto.
Distancia recorrida a partir de velocidad y tiempo.
Cálculo de consumo o rendimiento.
No es obligatorio utilizar los ejemplos anteriores.

2. Formulario dinámico

Al seleccionar una opción del menú, el formulario deberá modificarse de acuerdo con el cálculo seleccionado y mostrar una imagen de la fórmula a utilizar.

Deberán cambiar, según corresponda:

Los campos necesarios para introducir los datos.
Las etiquetas de cada campo.
Las unidades asociadas.
Las ayudas o indicaciones para el usuario.
La imagen o representación de la fórmula utilizada.
No deberán permanecer visibles campos que no correspondan al cálculo seleccionado.

3. Captura y validación de datos

Antes de realizar cualquier cálculo se deberán validar todos los datos introducidos.

Como mínimo deberán contemplarse:

Campos obligatorios.
Valores numéricos válidos.
Restricciones de valores positivos, negativos o diferentes de cero cuando corresponda.
Rangos válidos cuando el dato tenga límites razonables.
Relaciones entre dos o más campos cuando la fórmula lo requiera.
Las validaciones deberán depender del cálculo seleccionado.

Por ejemplo:

En una ecuación de segundo grado, a no puede ser cero.
Si solamente se desean raíces reales, el discriminante deberá ser mayor o igual a cero.
Un radio o una longitud no pueden tener valores negativos.
Un tiempo utilizado para un cálculo físico no deberá ser negativo.
Una temperatura expresada en Celsius no podrá ser menor al cero absoluto.
Una tasa porcentual deberá respetar el rango definido para el ejercicio.
No deberá realizarse ningún cálculo mientras exista algún dato incorrecto.

Los errores deberán indicarse de manera clara en los campos correspondientes o mediante algún mecanismo apropiado de retroalimentación al usuario.

4. Procesamiento de datos

Al presionar el botón Calcular, la aplicación deberá:

Recuperar los datos introducidos en el formulario.

Validarlos.
Realizar el cálculo correspondiente.
Procesar el resultado.
Presentarlo al usuario de forma clara.
El resultado deberá incluir:

El valor calculado.
La unidad correspondiente, cuando aplique.
Un ejemplo de cómo podría lucir la interfaz se muestra a continuación:



Consideraciones adicionales:

El nivel de API mínimo será el 28.
Pueden definir todos los elementos gráficos y/o de multimedia que deseen para hacer más llamativa la interfaz.
La app deberá contar con un ícono personalizado.
No deberán existir textos visibles al usuario escritos directamente mediante hard-coding en el código Kotlin o en los layouts.
La aplicación debe estar en por lo menos dos idiomas desde el archivo de recursos de texto (español y otro).
El ejercicio es individual, por lo que consideren que si encuentro ejercicios con sospecha de ser copia de otros, los anularé. La entrega se hará al subir toda la carpeta de su proyecto comprimida o al compartir en este espacio la liga de la carpeta comprimida del proyecto para ser descargada a través de un servicio de almacenamiento en la nube o en algún repositorio público en GitHub. La fecha máxima de entrega será el día domingo 18 de octubre de 2026 a las 23:59 hrs.

Tomen en cuenta por favor que la plataforma bloqueará las entregas después de esa fecha y hora.