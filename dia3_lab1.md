# Dia 3 - Laboratorio 1

El objetivo de este laboratorio es familiarizarse con Jinja y sus estructuras de control

Estudiaremos un rol con un templating algo complejo, y jugaremos con como simplificar el templating.

## Arrancar el laboratiorio

```bash
ansible-playbook crear-lab5s2.yml
```

Tras unos segundos este playbook habrá creado 1 máquina Centos 7, podéis ver su IP's en el 
fichero ```inventories/dia2lab5.yml```

Para acceder a ellas podréis hacerlo mediante el usuario "centos", con la clave pública que
se os ha dado justo con el fichero aws_vault.yml

Recomendamos dejar la clave pública en el directorio $HOME del usuario que vayáis a usar 
en la VM de laboratorio que se usa para control. De esta forma los comandos de la documentación
se ajustarán al entorno.

Ejemplo de comando para acceder a una de las máquinas de lab:

```ssh -i $HOME/curso-itnow.pem centos@a.b.c.d```

## Ejercicio 1 - Lectura del rol "laboratorio-jinja2"

Análicemos en grupo el rol "laboratorio-jinja2" y las estructuras de control que hay en la plantilla Jinja.

Especial atención en:
- Includes
- Composición de cadenas para generar nombres de variables

## Ejercicio 2 - crear un playbook que aplique el rol

Crearemos un rol que aplique el rol laboratorio-jinja2 y el rol nginx que tenemos de otros dias
a la máquina de laboratorio.

## Ejercicio 3 - crear un filtro custom de Jinja

Como habremos observado, el siguiente bloque de código puede ser complejo:

```jinja2
{% if ansible_os_family == 'RedHat' %}<img src="https://upload.wikimedia.org/wikipedia/en/thumb/6/6c/RedHat.svg/93px-RedHat.svg.png" />{% else %}{{ ansible_os_family }}{% endif %}
```

Como se repite en dos líneas, podemos crear un filtro custom de Jinja que nos devuelva el logo adecuado.

Para ello crearemos el fichero custom_plugins.py en la carpeta ""


# Fin del laboratorio

En este laboratorio se habrán adquirido los siguientes conocimientos:
- Uso de los bucles para tareas repetitivas
- Refactorización de código para mejor legibilidad del mismo

Procederemos a la destrucción del laboratorio:

```bash
ansible-playbook borrar-labs5s2.yml
```