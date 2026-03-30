# 1. Segmentación y Aislamiento de Red (pfSense)

El primer pilar de este SOC es garantizar que ningún tráfico malicioso o legítimo pueda eludir los controles de seguridad. Para ello, se diseñó una arquitectura "Air-Gapped" a nivel lógico.

## 1.1 Configuración de Bridges en Proxmox
Se separó el tráfico físico del virtual mediante dos puentes de red:
* **`vmbr0` (WAN):** Conectado directamente a la salida externa (`localhost` / `x.x.x.x`). Representa la "calle" o el internet público.
* **`vmbr1` (LAN):** Un switch virtual completamente aislado. Carece de salida a internet nativa. Su único punto de contacto con el exterior es a través de la interfaz LAN del firewall pfSense (`x.x.x.x`).

## 1.2 Configuración del Endpoint (Windows Server)
Para asegurar que el servidor víctima estuviera protegido por el firewall, se le asignó una configuración de red estática dentro del segmento seguro:
* **Dirección IP:** `x.x.x.x`
* **Máscara de Subred:** `255.255.255.0`
* **Puerta de Enlace (Gateway):** `x.x.x.x`

## 1.3 Validación de Enrutamiento Estricto
Para demostrar que el aislamiento fue exitoso y que el Windows Server no tiene fugas de red hacia el exterior, se realizó una traza de paquetes ICMP hacia un DNS público.

```cmd
tracert 8.8.8.8
