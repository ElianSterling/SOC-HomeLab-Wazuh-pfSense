
```markdown
# 3. Configuración de IDS e Inspección de Tráfico (Suricata)

Con la visibilidad del host asegurada mediante Wazuh, el siguiente paso fue implementar la detección a nivel de red (Network-based Intrusion Detection) utilizando **Suricata**, instalado como un paquete dentro de pfSense.

## 3.1 Asignación Estratégica de Interfaces
Por defecto, un firewall solo bloquea o permite puertos (Capa 3 y 4). Para lograr inspección profunda de paquetes (DPI), se habilitó Suricata explícitamente en la interfaz **LAN** (`192.168.1.1`). Esto garantiza que cualquier escaneo o ataque que logre atravesar la WAN sea analizado antes de tocar el Windows Server.

## 3.2 Actualización y Selección de Firmas (Rulesets)
Un IDS sin reglas actualizadas es ciego. Se configuró lo siguiente:
1. **Actualización:** Se descargaron las firmas de amenazas abiertas de *Emerging Threats (ET Open)*.
2. **Activación de Categorías:** Se perfilaron las reglas enfocándolas en las tácticas esperadas de un atacante:
   * `emerging-scan.rules`: Crítico para detectar reconocimiento de red y huellas de herramientas como Nmap.
   * `emerging-rdp.rules`: Específico para detectar intentos de conexión anómalos o fuerza bruta contra el protocolo de Escritorio Remoto (Puerto 3389).

Con esta configuración, Suricata actúa como el "vigilante" silencioso de la red interna, capaz de generar alertas ante patrones de tráfico malicioso.
