
```markdown
# 2. Despliegue de SIEM en Entorno Aislado (Wazuh)

El segundo pilar consiste en obtener visibilidad profunda de los eventos del sistema operativo (Host-based Intrusion Detection). Para esto, se utilizó **Wazuh**, administrado desde un servidor Ubuntu (`192.168.1.70`).

## 2.1 El Reto del Entorno Aislado
Dado que la red LAN fue configurada sin resolución DNS externa ni salida directa a internet por razones de seguridad, la instalación automatizada del agente de Wazuh en el Windows Server no era posible. 

## 2.2 Solución y Despliegue
Se aplicó una estrategia de aprovisionamiento seguro:
1. Se descargó el instalador `.msi` del agente de Wazuh proporcionando temporalmente una interfaz con DHCP al servidor.
2. Se revirtió la interfaz de red inmediatamente al puente aislado (`vmbr1`) para mantener la integridad del laboratorio.
3. Se ejecutó la instalación silenciosa mediante **PowerShell** con privilegios administrativos, apuntando el agente directamente a la IP privada del Manager:

```powershell
