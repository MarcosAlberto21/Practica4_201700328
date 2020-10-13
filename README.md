# Practica4_201700328 - Creacion de router on stick 

#### Conguración de la red
     VLAN	 Dirección de red	       Primera Direccion asignable	     Última dirección asignable          Dirrección de Broadcast
     10	   192.168.18.0/24	        192.168.18.1/24	                 192.168.18.254/24	                  192.168.18.254/24
     20	   192.168.28.0/24	        192.168.28.1/24	                 192.168.28.254/24	                  192.168.28.254/24

#### Modelo

 ![image](https://drive.google.com/uc?export=view&id=1YNCwqQwSranoYaojTEHtNGa_EQXwRZ9a)


# Configurar los modos de acceso y/o troncal en ESW1, ESW2, ESW3 que correspondan para garantizar el tráfico de VLAN
#### configuracion trunk a los SW capa 3
          comandos:
          conf t
          interface range fastEthernet 1/0 - 15 
          speed 100
          duplex full
          switchport mode trunk
          no shutdown
          exit
          exit
          write
          !

 ![image](https://drive.google.com/uc?export=view&id=1h3K5BRnEkk0WXSPbotkohsaFC0KKfG0U)

# Configuración de VTP
#### Colocar como dominio y contraseña: redes1_<carné>
     Modo servidor en ESW1
     comandos:
          vlan database
          !
          vtp domain redes1_201700328
          vtp password redes1_201700328
          vtp V2-mode
          vtp CLIENT
          !
          exit
          !
          write
          !
     Modo cliente en ESW2, ESW3
     comandos:
          vlan database
          !
          vtp domain redes1_201700328
          vtp password redes1_201700328
          vtp V2-mode
          vtp SERVER
          !
          exit
          !
          write
          !
          
 ![image](https://drive.google.com/uc?export=view&id=1mwVrZ0NmdRG_kJVjcWoYrQptPUKCs3sy)
#### Crear VLAN 10, 20 en todos los ESW capa 3
    VLAN 10: VENTAS 
    VLAN 20: CONTABILIDAD
    
          vlan database
          !
          vlan 10 name VENTAS
          !
          vlan 20 name CONTABILIDAD
          !
          exit
          !
          write
          !
![image](https://drive.google.com/uc?export=view&id=17yHFXUw3RYqgofveHjnCAvW9DHH8axj4)
# Configurar y crear los siguientes port-channel
     Po1: entre ESW1 y ESW2
     Po2: entre ESW1 y ESW3
     Po3: entre ESW2 y ESW3
     
     comandos:
     
     SW1  SW2
     1/1  1/1    1
     1/2  1/2    

     SW2  SW3
     1/3  1/3    2
     1/4  1/4

     SW3 SW1     
     1/5 1/5	    3
     1/6 1/6

     conf t
     interface fastEthernet 1/6
     channel-group 3 mode on
     exit
     exit
     write
     !

     sh interfaces port-channel 3
     
![image](https://drive.google.com/uc?export=view&id=131V9Z6Ao8pt7ES55Cis6i89_43GB9KT8)    
# Verificar que switch es el root bridge (STP) y que puertos están bloqueados por Spanning-tree.

     aplicar el comando ->sh spanning-tree brief
     
     BUSCAR LOS PUERTOS QUE ESTAN BLOQUEADOS POR EL PROTOCOLO
     
 ![image](https://drive.google.com/uc?export=view&id=1AmCjgYAg8-jT34G6pqzdkS8JRFU6MMmS)        

# Configurar las Subinterfaces del router con la dirección Gateway de los hosts de cada red proporcionada más adelante

     comandos:
     interface fastEthernet 0/0
     no shutdown

     interface fastEthernet 0/0.10
     encapsulation dot1Q 10
     ip address 192.168.10.254 255.255.255.255.0

     interface fastEthernet 0/0.20
     encapsulatio dot1Q 20
     ip address 192.168.20.254 255.255.255.0

 ![image](https://drive.google.com/uc?export=view&id=1YYkW6dYOrIsvcoAPLEvXRnBhTw1ynzKY)   
# Configurar los routes CAPA 2 en modo acceso (los puertos que conectan a las VPCs y modo troncal los puestor que conectan a los ESW)
 ![image](https://drive.google.com/uc?export=view&id=1vGveklwrKzJjDuEtZq08e2igfsA7c7G5) 

   
