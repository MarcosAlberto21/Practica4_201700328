# Practica4_201700328 - Creacion de router on stick 

# Configurar los modos de acceso y/o troncal en ESW1, ESW2, ESW3 que
#correspondan para garantizar el tráfico de VLAN
# Configuración de VTP
#### Colocar como dominio y contraseña: redes1_<carné>
     Modo servidor en ESW1
     Modo cliente en ESW2, ESW3
     Crear VLAN 10, 20
    VLAN 10: VENTAS 
    VLAN 20: CONTABILIDAD
# Configurar y crear los siguientes port-channel
     Po1: entre ESW1 y ESW2
     Po2: entre ESW1 y ESW3
     Po3: entre ESW2 y ESW3
# Verificar que switch es el root bridge (STP) y que puertos están bloqueados por Spanning-tree.
# Configurar las Subinterfaces del router con la dirección Gateway de los hosts de cada red proporcionada más adelante
