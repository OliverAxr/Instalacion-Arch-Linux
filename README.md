# Instalacion-Arch-Linux
Instalación de Arch Linux como base para personalizar con posteriormente con Hyprland

Aumentar el tamaño de letra
setfont ter-132n

poner teclado en español
loadkeys es


Iniciar conexión Wifi
iwctl
device list
station wlan0 scan
station wlan0 get-networks
station wlan0 connect "SSID"
- Ingresar contraseña de wifi
station wlan0 show
exit
- Ctrl + L para limpiar la pantalla
ping google.com
- Ctrl + C para detener el ping
- Ctrl + L para limpiar la pantalla


Particionar el disco para crear un Dualboot con Windows
Nota: En caso de usar todo el disco para la instalación, omitir esta sección y pasar a la siguiente

- Conocer el nombre del disco donde se va a realizar la instalación
lsblk

- Entrar al disco para particionar
cfdisk /dev/nvme0n1

Crear partición de booteo
- Seleccionar "Free space" con las flechas de arriba y abajo, y con las flechas izquierda y derecha seleccionas "New" y presionar Enter
- Ingresar el tamaño de 600M y presionar Enter (Se genera partición como /dev/nvme0n1p5)
- Seleccionar Type y escoger EFI System

Crear partición de instalación de ArchLinux
- Seleccionar "Free space" con las flechas de arriba y abajo, y con las flechas izquierda y derecha seleccionas "New" y presionar Enter
- Ingresar el tamaño del resto del disco y presionar Enter (Se genera partición como /dev/nvme0n1p6 y con el tipo de Linux filesystem)
- Seleccionar "Write" con las flechas izquierda y derecha y presionar Enter
- Confirmar escribiendo "yes" 
- Seleccionar "Quit" para salir de las funciones de particionado de disco.


Actualizar instalador
pacman -Sy archinstall --needed
- Si se muestra una nueva versión se confirma con yes
- Ctrl + L para limpiar la pantalla


Iniciar Instalación
archinstall

Idioma de Archinstall 
Spanish

Localidades
* Distribución del teclado 
- Cambiar a "es"

* Idioma Local: 
- Cambiar a "es_MX.UTF-8"

* Codificación local: 
- Dejar en UTF-8


Espejos y Repositorios
* Seleccionar regiones 
- Seleccionar las regiones de sitios de repositorios mas cercanos a tu ubicación Geográfica usando barra espaciadora para marcarlos y al finalizar presionar Enter

* Repositorios opcionales
- Se recomienda marcar multilib con barra espaciadora y presionar Enter


Configuración del Disco
Aquí se define si es una Instalación completa (Si todo el disco esta dedicado a la instalación de ArchLinux) o si se realiza un DualBoot con Microsoft Windows

* Instalación completa
- Particionamiento
- Utilizar un diseño de partición predeterminado de mejor esfuerzo
- Seleccionar el disco donde se realizara la instalación (dev/nvme0n1) y dejar el formato de disco ext4

* Para Dualboot
- Particionamiento
- Partición Manual
- Seleccionar disco donde se realizara la instalación (dev/nvme0n1) y presionar Enter
- Desplazarse a la partición de 600M /dev/nvme0n1p5 y presionar Enter
- Seleccionar Asignar punto de montaje (Assign mountpoint)
- Escribir: /boot
- Desplazarse a la partición de restante /dev/nvme0n1p6 y presionar Enter
- Seleccionar Asignar punto de montaje (Assign mountpoint)
- Escribir: /
Confirmar y salir


Swap 
- Intercambio de zram: Habilitado


Gestor de Arranque
- Gestor de Arranque: Grub


Nombre del host
- Ingresar el nombre que llevara el equipo


Autenticación: 
- Cuenta de usuario
- Añadir un usuario
- Escribir y confirmar contraseña
- Confirmar si el usuario creado debe ser un superusuario (sudo)
- Confirmar y salir


Perfil: 
* Instalación mínima
- Tipo
- Minimal

* Instalación Básica
- Desktop
- Hyprland
- Seleccionar "polkit"

* Controlador de graficos: 
- Seleccionar "All Open-sourse"

* Gestor de inicio de sesión 
-Seleccionar "sddm"


Aplicaciones
* Bluetooth
- Seleccionar "Si"

* Audio
- Seleccionar "pipewere"


Núcleos
- Dejar Linux (predeterminado)


Configuración de la red
- Seleccionar NetworkManager

Paquetes adicionales
curl
fastfetch
firefox
git
micro
openssh
xdg-user-dirs


Zona horaria
- Seleccionar la zona horaria de tu zona geográfica


NTP
- Seleccionar "Si"


Instalar
- Confirmar instalación seleccionando "Sí"

Una vez finalizada la instalación se ingresa al sistema para apagar el equipo y retirar la memoria USB


Nota: para VM de VirtualBox, se ingresa antes de reiniciar y se instala spice-vdagent

sudo pacman -S spice-vdagent
sudo systemctl enable spice-vdagent
sudo pacman -S virtualbox-guest-iso

activar en VirtualBox - Vista - escala de monitor - auto redimensionar la vm con la ventana

Reboot System
