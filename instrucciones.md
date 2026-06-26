# Instalación p5.js en Raspberry Pi — Modo Kiosk con Audio USB

## Qué hace este setup

- Sirve un proyecto p5.js de forma local
- Abre Chromium en pantalla completa (kiosk)
- Usa una interfaz de audio USB (UGREEN CM383 / ICUSBAUDIO7D)

---

## Archivos necesarios

```
~/Desktop/
├── reiteracion/          ← carpeta del proyecto p5.js
├── ejecutar_reiteracion.sh
└── Reiteracion.desktop
```

---

## ejecutar_reiteracion.sh

```bash
#!/bin/bash

pkill chromium
pkill -f "python3 -m http.server"

cd ~/Desktop/reiteracion
python3 -m http.server 8000 &

sleep 2

chromium --kiosk http://localhost:8000
```

Hacerlo ejecutable:

```bash
chmod +x ~/Desktop/ejecutar_reiteracion.sh
```

---

## Reiteracion.desktop

```ini
[Desktop Entry]
Version=1.0
Type=Application
Name=Reiteracion
Exec=/home/matilov/Desktop/ejecutar_reiteracion.sh
Icon=applications-multimedia
Terminal=false
```

Hacerlo ejecutable:

```bash
chmod +x ~/Desktop/Reiteracion.desktop
```

---

## Configurar audio USB (hacer una sola vez)

Instalar pavucontrol si no está:

```bash
sudo apt install pavucontrol
```

Abrir:

```bash
pavucontrol
```

En la pestaña **Output Devices**:

1. Seleccionar **ICUSBAUDIO7D**
2. Hacer clic en **Set as fallback**

Esto hace que Chromium use la tarjeta USB. Sin este paso, el audio sale por HDMI.

---

## Cómo usar

1. Doble clic en **Reiteracion.desktop**
2. Esperar a que cargue la obra en pantalla completa
3. Cuando aparezca el triángulo de inicio, hacer clic sobre él

---

## Verificar que el audio USB está activo (opcional)

```bash
speaker-test -D plughw:3,0 -c 2
```

Si suena, el hardware está bien. Si Chromium no sale por ahí, abrir `pavucontrol` y repetir el paso de configuración.
