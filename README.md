# 🛡️ SOC Home Lab: Wazuh, pfSense & Suricata en Proxmox

## 📝 Visión General del Proyecto
Este proyecto documenta el diseño, despliegue y validación de un Centro de Operaciones de Seguridad (SOC) en un entorno de laboratorio virtualizado. El objetivo principal es construir una arquitectura de red estrictamente segmentada para simular un entorno corporativo seguro, implementar monitorización continua y validar las capacidades de detección frente a ciberataques reales.

Este entorno demuestra fundamentos prácticos de **Seguridad Defensiva (Blue Team)**, administración de sistemas Linux/Windows y análisis de tráfico de red.

## 🏗️ Arquitectura y Topología Lógica
El laboratorio está alojado íntegramente sobre el hipervisor **Proxmox VE**, segmentando la red de la siguiente manera:

* **Router / Firewall Perimetral:** pfSense (WAN: `localhost` / LAN: `x.x.x.x`)
* **IDS / IPS (Network Security):** Suricata (Integrado nativamente en pfSense)
* **SIEM / XDR (Host Security):** Wazuh Manager desplegado sobre Ubuntu Server (`x.x.x.x`)
* **Endpoint Protegido (Víctima):** Windows Server 2022 (`x.x.x.x`)
* **Nodo Ofensivo (Atacante):** Kali Linux (Ubicado en la red externa `x.x.x.x`)

## 🛠️ Stack Tecnológico
* **Infraestructura:** Proxmox VE, Redes Virtuales (Bridges).
* **Seguridad Defensiva:** pfSense (Reglas de Firewall, NAT), Suricata (Reglas ET Open), Wazuh (Agentes, Decoders, Reglas de Alerta).
* **Seguridad Ofensiva:** Nmap (Reconocimiento), Hydra (Fuerza Bruta RDP).

## 📂 Índice de Documentación Detallada
Para comprender el despliegue paso a paso, la documentación se ha dividido en las siguientes fases:
1. [Segmentación y Aislamiento de Red](1-Configuracion_Red_pfSense.md)
2. [Despliegue de SIEM y Agentes en Entorno Aislado](2-Despliegue_SIEM_Wazuh.md)
3. [Configuración de IDS e Inspección de Tráfico](3-Configuracion_IDS_Suricata.md)
4. [Simulación de Ataques y Triage de Alertas](4-Simulacion_Ataques_y_Deteccion.md)
