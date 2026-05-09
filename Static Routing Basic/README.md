# 🌐 Static Routing Basic

Repositorio dedicado a un laboratorio práctico de **routing estático en Cisco Packet Tracer**, orientado al aprendizaje de conectividad entre múltiples redes mediante routers Cisco.

Este laboratorio simula un entorno real de infraestructura de red donde diferentes subredes necesitan comunicarse utilizando rutas estátcas configuradas manualmente.

## 🎯 Objetivos del laboratorio

- Configurar múltiples routers Cisco

- Implementar direccionamiento IP

- Configurar rutas estáticas

- Verificar conectividad entre redes

- Analizar tablas de routing

- Realizar troubleshooting básico

- Simular operaciones reales de networking

## 📁 Estructura del laboratorio

```
static-routing-basic/
├── topology.pkt
├── configs/
└── README.md
```

## 🧠 Topología del laboratorio

El laboratorio utiliza:

- 2 routers Cisco
- 2 switches
- 2 redes LAN
- Hosts finales conectados a cada red

**Ejemplo de direccionamiento**

| Dispositivo | Interfaz | Direccionamiento IP |
|-------------|----------|---------------------|
| Router 1    | G0/0   | 192.168.1.1/24    |
| Router 1    | G0/1   | 10.0.0.1/30    |
| Router 2    | G0/0   | 192.168.2.1/24 |
| Router 2    | G0/1   | 10.0.0.2/30 |
| PC1         | NIC    | 192.168.1.10|
| PC2         | NIC    | 192.168.2.10

# 🔧 Configuración básica

Las configuraciones se encuentran disponibles en:

- Router 1: [ver aquí](./conf/router1.conf)
- Router 2: [ver aquí](./conf/router2.conf)

# ▶️ Verificación

Comandos empleados:

```
show ip route
show ip interface brief
ping 192.168.2.10
```

# 🧪 Validaciones realizadas

- Conectividad entre routers
- Comunicación entre PCs de distintas redes
- Verificación de rutas estáticas
- Estado operativo de interfaces
- Diagnóstico básico de conectividad

# 🔍 Troubleshooting básico

Problemas simulados:

- Interfaces apagadas
- Gateway incorrecto
- Ruta estática ausente
- Máscara de red incorrecta

Diagnóstico realizado mediante:

- ping
- show ip route
- show running-config
- show ip interface brief

# 🧠 Enfoque

Este laboratorio está orientado a:

- Networking práctico
- Routing básico
- Operaciones NOC
- Troubleshooting de red
- Infraestructura Cisco
- Aprendizaje reproducible

No se centra únicamente en teoría, sino en configuración y validación práctica.

## 👤 Autor

Manuel Míguez Liméns

[GitHub](https://github.com/manuelmiguezlimens?tab=repositories) | [LinkedIn](https://www.linkedin.com/in/manuelmiguezlimens/) | [Gmail](mailto:miguezlimensmanuel@gmail.com)