# 4. Simulación de Ataques y Triage de Alertas

Para comprobar la resiliencia de la arquitectura y la eficacia del SOC, se ejecutó una simulación de ataque real (Red Teaming) desde una IP externa (`x.x.x.x`) utilizando **Kali Linux**.

## 4.1 Fase 1: Reconocimiento Activo y Escaneo
Se utilizó Nmap para descubrir servicios expuestos en el Windows Server, utilizando un perfil agresivo para generar ruido en la red:

```bash
nmap -sV -sC -O -A -T4 192.168.1.10

4.2 Fase 2: Ataque de Fuerza Bruta (Movimiento Lateral)
Tras identificar el puerto 3389 (RDP) abierto, se simuló un intento de intrusión mediante fuerza bruta utilizando Hydra y el diccionario rockyou.txt contra el usuario administrador nativo:

hydra -t 4 -l Administrator -P /usr/share/wordlists/rockyou.txt rdp://192.168.1.10 -V
