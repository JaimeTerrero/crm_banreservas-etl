1. Origen de archivo plano. Lee un archivo de texto, en este caso un .csv, a través de la ruta especificada. El primer paso consiste en indicar correctamente la ruta del archivo de origen que contiene los datos a importar.


2. Conversion de datos. Realiza la conversión de los tipos de datos del archivo hacia los tipos esperados por la base de datos.
En esta etapa también se configuran alias y mapeos de tipo de datos para garantizar la integridad al cargar la información.


3. Division Condicional.

      -Si el monto es válido (> 0), los datos continúan hacia la tabla de ventas.
    
      -Si el monto es inválido (< 0), el registro se redirige a la tabla ETL_ErrorLog.


4. Destino de OLE DB.
      Corresponde a la carga de datos válidos hacia la base de datos principal.
      El usuario debe:
      
      -Configurar su Administrador de Conexiones (Servidor y Base de Datos).
      
      -En Modo de acceso a datos, seleccionar “Tabla o vista”.
      
      -En Nombre de la tabla o vista, colocar la tabla Ventas.
      
      -En Asignaciones, mapear los campos para asegurar que correspondan correctamente con las columnas de destino.


5. Destino de OLE DB 1.
      En esta etapa recibe los errores provenientes de las fases de Conversión de datos y Destino OLE DB, y los redirecciona hacia el Destino OLE DB 1, garantizando que toda excepción quede registrada en la tabla ETL_ErrorLog.


6. Unión de todo.
  Corresponde a la carga de datos con errores hacia la tabla de control de errores.
  El usuario debe:
  
      -Configurar nuevamente su Administrador de Conexiones (Servidor y Base de Datos).
      
      -Seleccionar “Tabla o vista” como modo de acceso.
      
      -En Nombre de la tabla o vista, indicar ETL_ErrorLog.
      
      -Verificar los mapeos en Asignaciones.

NOTA: Recordar correr los SCRIPTS enviados en el correo para el correcto funcionamiento de la aplicación.


