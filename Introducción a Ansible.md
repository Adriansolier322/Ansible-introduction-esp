***
Ansible proporciona automatización de código abierto que reduce la complejidad y funciona en todas partes. Ansible permite automatizar prácticamente cualquier tarea. Aquí puedes ver algunos casos de uso comunes:
* **Elimina la repetición de tareas** y simplifica el flujo de trabajo
* **Gestiona y mantiene** la configuración de equipos
* **Implementa** de forma continua **software complejo**
* Realiza **actualizaciones** continuas sin **tiempo de espera**

Ansible usa scripts con una sintaxis sencilla y entendible llamados ***playbooks*** para la automatización de tareas. Declaras el estado de una maquina local o remota y Ansible se encarga de mantenerla en ese estado.<br>
***
Como tecnología de automatización Ansible esta diseñada bajo los siguientes principios:
###### Arquitectura sin agentes
Baja sobrecarga de mantenimiento al evitar la instalación de software adicional en toda la infraestructura informática.
###### Simplicidad
Los playbooks usan una sintaxis [YALM](https://es.wikipedia.org/wiki/YAML) para programar como si leyeras documentación. Ansible también esta descentralizado, ya que usa SSH con las credenciales existentes en el SO para acceder a las maquinas remotas.
###### Escalabilidad y flexibilidad
Es fácil y rápido escalar sistemas automatizados mediante diseños modulares compatibles con una amplia gama de SO, plataformas en la nube y dispositivos de la red.
###### [Idempotencia](https://es.wikipedia.org/wiki/Idempotencia) y previsibilidad
Cuando el sistema esta en el estado que describe su playbook Ansible no cambia nada incluso si el playbook se ejecuta varias veces