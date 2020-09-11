# hd-larger-to-smaller
Clone HD/SSD larger to smaller

## Shrink Win 10 partition

En caso de no conseguir verificar os seguintes pontos:

https://answers.microsoft.com/en-us/windows/forum/all/windows-disk-management-unable-to-shrink-c-drive/217c3521-b254-4662-bac9-bc90dc633fab

## Clone
``` bash
# Lista de particiones de la fuente (sectores y tipos)
sgdisk /dev/src

# Crear Particiones en el destino
gdisk /dev/dst
n # Crear particion
... # Usar los sectores (adaptados si necesario) de la lista de /dev/src y los tipos de particiones.
w # Escribir tabla de particiones con las modificaciones

# Listar UUIDs, PARTUUIDs, etc. de la fuente
sudo blkid | grep '/dev/src' | sort # Lista los UUID, PARTUUID, etc.

# Modificar UUIDs en el destino
gdisk /dev/dst
x # Expert command
c # Modificar PRTUUID por cada partición
w

# Copiar Datos
dd if=/dev/srcX of=/dev/dstX bs=4096 conv=noerror,sync # Por cada particion
```

## Win 10 Boot Fix
https://www.youtube.com/watch?v=BBeiztzS5vo
