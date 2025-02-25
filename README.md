# Escalada de Privilegios en Active Directory
![imagen](https://github.com/90l3m0np13/Escala-de-Privilegios/blob/main/Escalada%20de%20privilegios.jpeg)
## Descripción General

Este repositorio documenta un ejercicio práctico de escalada de privilegios en un entorno de dominio de Windows. El objetivo es demostrar cómo un atacante podría obtener acceso de administrador desde una cuenta de usuario estándar utilizando una combinación de herramientas y técnicas.

## Herramientas Utilizadas

* **BloodHound:** Para mapear las relaciones de confianza y los posibles caminos de ataque en el dominio.
* **PowerView:** Para la enumeración detallada de usuarios, grupos y otros objetos de Active Directory.
* **Runas:** Para ejecutar procesos con las credenciales de un usuario con privilegios elevados.

## Paso a Paso

### 1. Reconocimiento Inicial y Configuración del Entorno

* Acceso a una máquina víctima dentro del dominio con una cuenta de usuario estándar.
* Verificación de los permisos del usuario actual.
* Configuración del entorno de PowerShell para ejecutar los scripts de PowerView.

### 2. Recopilación de Datos con BloodHound

* Ejecución del script `Invoke-BloodHound` desde una sesión de PowerShell con la cuenta de usuario estándar.
* Generación de un archivo ZIP con los datos recopilados.
* Importación del archivo ZIP a la interfaz de BloodHound.
* Análisis de las relaciones de confianza y búsqueda de posibles caminos de ataque.
    * *Captura de pantalla de BloodHound mostrando un posible camino de ataque.*

### 3. Enumeración Detallada con PowerView

* Utilización de los siguientes comandos de PowerView:
    * `Get-DomainUser`: Enumeración de usuarios del dominio.
    * `Get-DomainGroupMember`: Enumeración de miembros de grupos específicos.
    * `Find-InterestingDomainAcl`: Búsqueda de listas de control de acceso (ACL) interesantes.
* Análisis de la información recopilada para identificar usuarios con privilegios elevados.
    * *Ejemplo de salida de los comandos de PowerView.*

### 4. Escalada de Privilegios con Runas

* Identificación de un usuario con privilegios elevados.
* Ejecución del comando `Runas` para ejecutar un proceso con las credenciales del usuario privilegiado.
    * *Ejemplo de comando: `runas /user:dominio\usuario_privilegiado cmd.exe`.*
* Acceso completo al sistema con privilegios de administrador.
    * *Captura de pantalla de la consola de comandos con privilegios elevados.*

## Medidas de Mitigación

* Implementar el principio de mínimo privilegio.
* Segmentar la red.
* Monitorizar actividades sospechosas.
* Mantener los sistemas actualizados.
* Realizar auditorías de seguridad de forma regular.

## Conclusiones

Este ejercicio demuestra la importancia de implementar medidas de seguridad robustas para proteger los entornos de dominio de Windows contra ataques de escalada de privilegios.

## Referencias

* [Documentación de BloodHound](enlace-a-documentacion-bloodhound)
* [Documentación de PowerView](enlace-a-documentacion-powerview)
* [Documentación de Runas](enlace-a-documentacion-runas)

## Contribuciones

Si deseas contribuir a este repositorio, puedes realizar un fork y enviar un pull request con tus mejoras.
