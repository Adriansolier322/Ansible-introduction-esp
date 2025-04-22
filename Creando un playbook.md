Los playbooks son planos de automatización en formato YAML, usado por ansibe para desplegar y configurar los 'managed nodes'.
- **Playbook**
	Una lista de 'plays' que define el orden en que ansible realiza sus operaciones, desde arriba hasta abajo.
- **Play**
	Una lista ordenada de tareas a realizar asignados a un 'managed node' en un inventario.
- **Task**
	Una referencia a un modulo que define las operaciones que ansible a de realizar.
- **Modulo**
	Una unidad de código o binario que ansible ejecuta en los 'managed nodes'. Los módulos se agrupan en colecciones con un Fully Qualified Colletion Name (FQCN) para cada módulo.

Completa los siguientes pasos para crear un playbook que hace un ping, copia un archivo hacia los 'managed nodes' y los actualiza.

1. Crea el archivo playbook.yaml con el siguiente contenido:
	```bash
	- name: My first play
  hosts: myhosts
  tasks:
   - name: Ping my hosts
     ansible.builtin.ping:

   - name: copiar un archivo
     ansible.builtin.template:
       src: /home/adrian/Documentos/ansible/pruebas/test.txt
       dest: /tmp/test.txt

   - name: update-system
     ansible.builtin.apt:
       upgrade: full
       autoremove: true
	 remote_user: root
	```
> [!WARNING]  
> Comprueba que el usuario root de los 'managed nodes' tiene acceso por ssh mediante contraseña si no estas usando claves ssh.
2. Ejecuta tu playbook.
	`ansible-playbook -i inventory.ini playbook.yml -u (usuario) -k`
	
> [!WARNING]  
> Si estas usando claves ssh en vez de contraseña omite la opción '-k'.

Ansible devuelve lo siguiente:
```bash
PLAY [My first play] *****************************************************************************

TASK [Gathering Facts] ***************************************************************************
ok: [10.42.0.102]
ok: [10.42.0.101]

TASK [Ping my hosts] *****************************************************************************
ok: [10.42.0.101]
ok: [10.42.0.102]

TASK [copiar un archivo] *************************************************************************
ok: [10.42.0.102]
ok: [10.42.0.101]

TASK [update-system] *****************************************************************************
ok: [10.42.0.101]
ok: [10.42.0.102]

PLAY RECAP ***************************************************************************************
10.42.0.101: ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
10.42.0.102: ok=4    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
En este output podemos ver lo siguiente:
- Los nombres de cada de cada 'play' y sus tareas. Generalmente deberías usar nombres descriptivos para hacer mas fácil la identificación y solución de problemas.
- La tarea 'Gathering Facts' se ejecuta de manera predeterminada y recopila información sobre el inventario que podrás usar en el 'playbook'.
- El estado de cada 'Task'. Cada 'Task' tiene un estado de `ok`que significa que se ha ejecutado de forma correcta.
- La 'Play recap' es un sumario de los resutados de cada tarea y sus estados por cada 'managed node'.
