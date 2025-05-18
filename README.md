# TP Final - Computación Aplicada (Grupo 9)

Repositorio del Grupo 9 para el Trabajo Práctico Integrador de la materia **Computación Aplicada** - Universidad de Palermo.

## Docentes
- Claudio Emilio Manuel Kainer
- Rodrigo Alejandro Duran


## Integrantes del grupo

- Frida Ruiz
- Matías Musso
- Federico Trezza
- Micaela Omahna

## Contenido del proyecto

Este repositorio contiene:

- Compresiones de directorios requeridos: `/root`, `/etc`, `/opt`, `/www_dir`, `/backup_dir`, `/proc/particion`
- Backup de `/var` dividido en partes


## Uso del script de backup

```bash
./backup_full.sh <origen> <destino>

```

## Automatización de backups con cron

El script `backup_full.sh` se ejecuta automáticamente mediante tareas programadas (cron):

- **Todos los días a las 00:00:** Realiza backup de `/var/log` en `/backup_dir`.
- **Lunes, miércoles y viernes a las 23:00:** Realiza backup de `/www_dir` en `/backup_dir`.

### Configuración de cron

Las siguientes líneas se agregaron al crontab del usuario root:

```cron
0 0 * * * /opt/scripts/backup_full.sh /var/log /backup_dir
0 23 * * 1,3,5 /opt/scripts/backup_full.sh /www_dir /backup_dir
```

### Ejecución manual del script

También puedes ejecutar el script manualmente:

```bash
/opt/scripts/backup_full.sh <origen> <destino>
```

Por ejemplo:

```bash
/opt/scripts/backup_full.sh /etc /backup_dir
```

## Nota sobre el script de backup

El script `backup_full.sh` se encuentra únicamente en la máquina virtual, en la ruta `/opt/scripts/`, y no forma parte de los archivos entregados en este repositorio. El repositorio solo incluye los directorios comprimidos requeridos y la documentación correspondiente.
