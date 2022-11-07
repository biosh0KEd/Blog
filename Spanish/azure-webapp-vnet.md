# Azure VNets 
Las redes virtuales de Azure son aislamientos lógicos de la nube dedicada a una subscripción especifica

Puede usar las redes virtuales para aprovisionar y administrar redes privadas virtuales (VPN) en Azure y, opcionalmente, vincular las redes virtuales con otras redes virtuales en Azure o con sus infraestructura de TI local para crear soluciones híbridas o entre entornos.

## Funcionalidades de Azure Virtual Networks
### Comunicación con Internet: 
- De manera predeterminadda todos los recursos de una red virtual tienen comunicación de salida hacia internet. 
    
- Para comunicarse con un recurso entrante, asígnele una dirección IP pública o un equilibrador de carga público. También puede usar la dirección IP pública o del equilibrador de carga público para administrar las conexiones salientes.

### Comunicación entre los recursos de Azure:
- Hay tres mecanismos clave a través de los cuales el recurso de Azure puede comunicarse: 
  - **Redes virtuales**

    No solo puede conectar máquinas virtuales, sino también otros recursos de azure, como App Service Environment, Azure Kubernetes Service y conjuntos de escalado de máquinas virtuales de Azure.
  - **Puntos de conexión de servicio**
    
    Se pueden usar para conectarse a otro tipo de recursos de Azure, como cuentas de almacenamiento y bases de datos de Azure SQL.        

  - **Emparejamiento de Vnets**
  
    Cuando se crea una red virtual, los servicios y las maquinas virtuales de la red pueden comunicarse de forma directa y segura entre ellas en la nube.

### Comunicación entre recursos locales
Extender su centro de datos de forma segura. Puede conectar los equipos y redes locales a una red virtual mediante cualquiera de las siguientes opciones: 
- Red privada virtual (VPN) de punto a sitio 
- VPN de sitio a sitio
- Azure ExpressRoute

### Filtrado del tráfico de red
Puede filtrar el tráfico de red entre subredes mediante cualquier combinación de grupos de seguridad de red y aplicaciones virtuales de red, como: 
- Firewalls 
- Puertas de enlace 
- Servidores proxy 
- Servicios de traducción de direcciones de red (NAT).

### Enrutamiento del tráfico de red
De forma predeterminada Azure enruta el tráfico entre subredes, redes virtuales conectadas, redes locales e Internet. Puede implementar tablas de rutas o rutas del protocolo de puerta de enlace de borde (BGP) para invalidar las rutas predeterminadas que crea Azure.

## Espacios de direacciones y subredes
Al crear una red virtual, se recomienda usar los intervalos de direcciones enumerados en RFC 1918, que el IETF ha reservado para los espacios de direcciones privados y no enrutables:
- 10.0.0.0 - 10.255.255.255 (prefijo 10/8)
- 172.16.0.0 - 172.31.255.255 (prefijo 172.16/12)
- 192.168.0.0 a 192.168.255.255 (prefijo 192.168/16)

Además, **no se pueden agregar los intervalos de direcciones siguientes**:

- 224.0.0.0/4 (multidifusión)
- 255.255.255.255/32 (difusión)
- 127.0.0.0/8 (bucle invertido)
- 169.254.0.0/16 (local de vínculo)
- 168.63.129.16/32 (DNS interno)

Azure asigna los recursos de una red virtual a una dirección IP privada desde el espacio de direcciones que aprovisione.

> **Por ejemplo**, si implementa una máquina virtual en una red virtual con el espacio de direcciones 192.168.1.0/24, a la máquina virtual se le asignará una dirección IP privada, como 192.168.1.4. Azure reserva las cuatro primeras y últimas direcciones IP para un total de cinco dentro de cada subred. Son x.x.x.0-x.x.x.3 y la última dirección de la subred.

**Por ejemplo**, el intervalo de direcciones IP de 192.168.1.0/24 tiene las siguientes direcciones reservadas:
- 192.168.1.0: dirección de red.
- 192.168.1.1: reservada por Azure para la puerta de enlace predeterminada.
- 192.168.1.2, 192.168.1.3 : reservada por Azure para asignar las direcciones IP de Azure DNS al espacio de red virtual.
- 192.168.1.255: dirección de difusión de red.

# App service integración con VNet