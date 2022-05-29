# LabsUnidad3Telematica
## Requisitos previos:  
* Par de claves EC2
* Bucket S3 
## Creación y configuración del clúster en AWS (Lab0)   
* Debera buscar `emr` en el buscador de servicios de aws
![image](https://user-images.githubusercontent.com/53051430/170846916-6a48d51f-05c8-4ab9-96cc-667a3248f995.png)
* Debera ir a `crear clúster`  
![image](https://user-images.githubusercontent.com/53051430/170846981-ffcbc360-ce4c-4fe1-b788-b4c30be50180.png)
* Selecionara `ir a las opciones avanzadas`  
![image](https://user-images.githubusercontent.com/53051430/170847017-da4a97ce-90c4-4192-aeca-851b303846fb.png)
* En el `Step 1` le pondrá los siguientes parametros (en la parte de editar configuración de software deberá cambiar `MyJupyterBackups` por el nombre del bucket previamente creado)
![image](https://user-images.githubusercontent.com/53051430/170847100-7698539f-7ed7-43e3-a1d9-fe54e3150cdf.png)
* En el `Step 2` cambiara lel tipo de instancias de `m5.xlarge` a `m4.xlarge` y la opcion de compra de `bajo demanda` a `spot`
![image](https://user-images.githubusercontent.com/53051430/170847291-fe522389-f9f7-4e5a-869d-c2b8b97ae4ac.png)  
ademas cambiará las siguientes opciones  
![image](https://user-images.githubusercontent.com/53051430/170847366-0209f337-44ef-4859-85cb-b75a16cc55dd.png)
* En el `Step 3` solo cambiara el nombre del clúster al que quiera
![image](https://user-images.githubusercontent.com/53051430/170847392-7b853bf7-6ee0-473a-9e68-c34b6afef816.png)
* En el `Step 4` seleccionara el par de claves EC2 previamente creada y creara el clúster (el clúster se demora entre 20 a 25 minutos en comenzar)
![image](https://user-images.githubusercontent.com/53051430/170847440-63bfa150-724f-46d9-ae62-888c925d359e.png)
* El clúster estara activo cuando pase de
![image](https://user-images.githubusercontent.com/53051430/170847505-1dd20bb2-466c-43c8-9c7a-a7f1771589d6.png)
a
![image](https://user-images.githubusercontent.com/53051430/170847513-92a39a14-aedf-43ce-8309-223ba729ca0b.png)  
### Activacion de puertos para conexion SSH, Hue, JupyterHub y Zeppelin  
* Debe ir al apartado de `Bloquear acceso público` y editarlo
![image](https://user-images.githubusercontent.com/53051430/170847595-b8cb337f-dce1-404d-937c-1b62c09f5dcd.png)  
* Luego debe ir al grupo de seguridad del master, puede acceder desde el resumen del clúster
![image](https://user-images.githubusercontent.com/53051430/170847638-9cc2383f-243e-461b-ba49-ce10cb976c86.png)
* Editara las `reglas de entrada` para agregar los puertos 22, 8888, 8890, 9443
![image](https://user-images.githubusercontent.com/53051430/170847680-bdeaee2d-8d06-41cf-9552-76762342ed7f.png)  
### Conexion con Hue  
* Ingresa al clúster y al apartado de `Historial de aplicaciones`
![image](https://user-images.githubusercontent.com/53051430/170847757-750252be-8f50-48ec-a92d-d618554c6cc4.png)  
* Copiará el url que sale en `Tonalidad`, este corresponde a Hue pero en la versión español está mal por la traducción
![image](https://user-images.githubusercontent.com/53051430/170847817-12a7b7e1-95b5-42a9-b558-360f9386ef17.png)
* En el login de Hue debe poner en username `hadoop` y en password cualquier contraseña que cumpla las condiciones que pide Hue
![image](https://user-images.githubusercontent.com/53051430/170848024-90661a6d-66ca-41a7-8b8d-91fabaa54097.png)  
![image](https://user-images.githubusercontent.com/53051430/170848044-391bf2f4-b708-4983-ba3d-db683ccbe891.png)  
### Conexion con JupyterHub  
* Ingresa al clúster y al apartado de `Historial de aplicaciones`
![image](https://user-images.githubusercontent.com/53051430/170847757-750252be-8f50-48ec-a92d-d618554c6cc4.png)  
* Copiará el url que sale en `JupyterHub`  
![image](https://user-images.githubusercontent.com/53051430/170847849-b8f5d110-7666-48df-9b10-56e38d017f52.png)
* En el login de Hue debe poner en username `jovyan` y el password `jupyter`  
![image](https://user-images.githubusercontent.com/53051430/170847978-13c8766a-2f08-482a-b633-8b29ae422fb0.png)  
![image](https://user-images.githubusercontent.com/53051430/170848628-4f7516d2-272e-4c3d-9803-6f551569d76a.png)
### Conexion con Zeppelin  
* Ingresa al clúster y al apartado de `Historial de aplicaciones`
![image](https://user-images.githubusercontent.com/53051430/170847757-750252be-8f50-48ec-a92d-d618554c6cc4.png)  
* Copiará el url que sale en `Zeppelin`  
![image](https://user-images.githubusercontent.com/53051430/170847858-caffa226-4d85-42a7-b57c-4873e56c55a3.png)  
* Zeppelin no necesita logearse  
![image](https://user-images.githubusercontent.com/53051430/170848013-5a5272ae-337c-4722-836e-9e7ee8843989.png)  
## Gestión de archivos hacia HDFS y AWS S3 (Lab1)  
### Hacia HDFS via SSH  
* Entrar a la isntancia del master con el comando SSH
![image](https://user-images.githubusercontent.com/53051430/170850389-3c2f7fb1-181e-47b4-9c02-3073f52375b5.png)
* Acceder mediante el super usuario
![image](https://user-images.githubusercontent.com/53051430/170850392-cb8c9467-c44a-48f3-9279-ef8c97ef547a.png)
* Crear el directorio  para guardar los archivos en el HDFS
![image](https://user-images.githubusercontent.com/53051430/170850394-f310a46e-8a8c-4d8b-ae64-0859b65e40a7.png)
* Con este comando se suben los archivos de la ruta especificada al HDFS
![image](https://user-images.githubusercontent.com/53051430/170850402-81b9873f-58d2-4682-b766-5f63f49ca69c.png)
![image](https://user-images.githubusercontent.com/53051430/170850410-4a6f0abb-529b-41e0-9ccb-9d069809588a.png)
* Confirmar que los archivos si se subieron
![image](https://user-images.githubusercontent.com/53051430/170850411-ca6f3061-e9f9-4c56-b2bd-c81a77ae18fa.png)  
### Hacia HDFS via HUE  
* Seleccionar archivo y subirlo
![image](https://user-images.githubusercontent.com/53051430/170850893-33db6aca-8032-4284-9cc8-e6f0cf9871a3.png)
### Hacia AWS S3 via SSH  
* Copiar los archivos de HSFS a S3
![image](https://user-images.githubusercontent.com/53051430/170851154-e9ce5411-64d0-4492-b4b4-8132402cc486.png)  
![image](https://user-images.githubusercontent.com/53051430/170851170-1d839453-c4b2-48f3-b33b-99c17848c526.png)  
![image](https://user-images.githubusercontent.com/53051430/170851171-59562842-244e-4266-ab6c-3dc32f1c2c74.png)  
* Confirmacion que los archivos se subieron  
![image](https://user-images.githubusercontent.com/53051430/170851200-53bf34b3-0ac7-4bc4-8246-15a8450e4106.png)  
### Hacia AWS S3 via HUE  



