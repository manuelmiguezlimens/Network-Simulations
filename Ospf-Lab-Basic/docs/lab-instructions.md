# OSPF Lab Basic – Instrucciones Paso a Paso

Este documento describe cómo implementar y validar un laboratorio de OSPF en Packet Tracer con tres routers y dos PCs.

---

## 1️⃣ Requisitos previos
- Cisco Packet Tracer instalado
- Conocimientos básicos de CLI de Cisco (interfaces, IP, OSPF)
- Conocimiento básico de redes y direccionamiento IP

---

## 2️⃣ Topología del laboratorio

![image1](./images/topología.png)


**Direcciones IP:**

| Dispositivo | Interfaz | IP | Máscara |
|-------------|----------|----|--------|
| R1 | Fa0/0 | 192.168.1.1 | 255.255.255.0 |
| R1 | Fa0/1 | 10.0.0.1 | 255.255.255.252 |
| R2 | Fa0/0 | 10.0.0.2 | 255.255.255.252 |
| R2 | Fa0/1 | 10.0.0.5 | 255.255.255.252 |
| R3 | Fa0/0 | 10.0.0.6 | 255.255.255.252 |
| R3 | Fa0/1 | 192.168.2.1 | 255.255.255.0 |
| PC1 | NIC | 192.168.1.10 | 255.255.255.0, Gateway 192.168.1.1 |
| PC2 | NIC | 192.168.2.10 | 255.255.255.0, Gateway 192.168.2.1 |

---

## 3️⃣ Paso 1: Crear dispositivos en Packet Tracer
1. Abrir Packet Tracer y crear un **nuevo proyecto**.
2. Arrastrar y colocar:
   - 3 routers (R1, R2, R3)
   - 2 PCs (PC1, PC2)
   - Opcional: switches entre PCs y routers para LANs
3. Conectar los dispositivos con cables:
   - Enlaces punto a punto: routers → routers (cable straight-through)
   - PCs → routers o switches según la LAN

---

## 4️⃣ Paso 2: Configuración de los PCs
1. Hacer clic en cada PC → Desktop → IP Configuration
2. Configurar:
   - PC1: IP 192.168.1.10, Máscara 255.255.255.0, Gateway 192.168.1.1
   - PC2: IP 192.168.2.10, Máscara 255.255.255.0, Gateway 192.168.2.1

---

## 5️⃣ Paso 3: Configuración de los routers

### **R1**
```bash
enable
configure terminal
hostname R1
interface fastEthernet 0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
interface fastEthernet 0/1
 ip address 10.0.0.1 255.255.255.252
 no shutdown
router ospf 1
 router-id 1.1.1.1
 network 192.168.1.0 0.0.0.255 area 0
 network 10.0.0.0 0.0.0.3 area 0
end
write memory
```

### **R2**
```bash
enable
configure terminal
hostname R2
interface fastEthernet 0/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown
interface fastEthernet 0/1
 ip address 10.0.0.5 255.255.255.252
 no shutdown
router ospf 1
 router-id 2.2.2.2
 network 10.0.0.0 0.0.0.3 area 0
 network 10.0.0.4 0.0.0.3 area 0
end
write memory
```

### **R3**
```bash
enable
configure terminal
hostname R3
interface fastEthernet 0/0
 ip address 10.0.0.6 255.255.255.252
 no shutdown
interface fastEthernet 0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown
router ospf 1
 router-id 3.3.3.3
 network 10.0.0.4 0.0.0.3 area 0
 network 192.168.2.0 0.0.0.255 area 0
end
write memory
```

---

## 6️⃣ Paso 4: Validación de conectividad

- Ver interfaces activas

    -  En cada router: ```show ip interface brief```

- Ver vecinos OSPF: ```show ip ospf neighbor```

    - Debes ver FULL entre R1-R2 y R2-R3.

- Ver rutas OSPF: ```show ip route```

    - Rutas que empiezan con O indican OSPF. Todas las redes deben estar accesibles.

- Prueba de ping desde PCs

    - En PC1 → Command Prompt: ```ping 192.168.2.10```

        Repetir en PC2 → 192.168.1.10.

