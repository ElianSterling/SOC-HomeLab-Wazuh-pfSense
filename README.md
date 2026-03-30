# 🛡️ SOC Home Lab: Wazuh, pfSense & Suricata en Proxmox

## 📝 Descripción del Proyecto
Este proyecto documenta la creación y configuración de un entorno virtualizado de un Centro de Operaciones de Seguridad (SOC). El objetivo principal es simular una red empresarial aislada, desplegar herramientas de monitoreo (SIEM) y detección de intrusos (IDS/IPS), y validar su eficacia mediante la simulación de ciberataques controlados. 

## 🏗️ Arquitectura y Topología
El entorno fue construido sobre el hipervisor **Proxmox VE**:

* **Router/Firewall:** pfSense (WAN: localhost / LAN: 192.168.1.1)
* **IDS/IPS:** Suricata (Integrado en pfSense)
* **SIEM:** Wazuh Manager en Ubuntu (192.168.1.70)
* **Endpoint (Víctima):** Windows Server 2022 (192.168.1.10)
* **Atacante:** Kali Linux (Red externa/WAN)

## 📂 Documentación Detallada
1. [Configuración de Red y Segmentación](1-Configuracion_Red_pfSense.md)
2. [Despliegue del SIEM (Wazuh)](2-Despliegue_SIEM_Wazuh.md)
3. [Configuración del IDS/IPS (Suricata)](3-Configuracion_IDS_Suricata.md)
4. [Simulación de Ataques y Detección](4-Simulacion_Ataques_y_Deteccion.md)
