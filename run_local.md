### Instrucciones para usarlo:
1. Ejecuta el comando siguiente para instalar las dependencias:
   ```bash
   docker-compose run bundler
   ```
2. Una vez instaladas las dependencias, inicia el servidor Jekyll con:
   ```bash
   docker-compose up
   ```
3. Abre tu navegador y navega a `http://localhost:4000` para ver el sitio en ejecución.

### Explicación:
- **Servicios**:
  - `kross-jekyll`: Contenedor principal que ejecuta el servidor Jekyll.
  - `bundler`: Se utiliza solo para instalar las dependencias requeridas.
- **Volúmenes**:
  - `.`: Sincroniza el directorio del proyecto con el contenedor.
  - `bundle_cache`: Guarda las gemas instaladas en un volumen persistente para evitar reinstalaciones repetidas.
- **Puertos**: 
  - Redirige el puerto 4000 del contenedor al puerto 4000 del host, permitiéndote acceder al servidor Jekyll desde el navegador.