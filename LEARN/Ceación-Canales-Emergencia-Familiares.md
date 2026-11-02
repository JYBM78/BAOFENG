# Guía de Configuración: Canal de Emergencia Familiar en Baofeng DM-32 UV
*Documento de estudio y referencia para programación en CPS DMR V1.60 y configuración manual por teclado, en la creación de Canales de Emergencia Familiares.*

---

## 1. Configuración en el Software CPS DMR V1.60

Para garantizar una comunicación robusta, crearemos dos canales en una frecuencia de uso libre internacional (banda UHF) que ofrece excelente penetración en estructuras y zonas urbanas.

### A. Canal Principal: Digital DMR (`EMERG FAM`)
Este canal ofrece audio limpio, optimiza la batería del radio y garantiza **privacidad familiar total** frente a interferencias de terceros.

| Parámetro en CPS | Configuración Exacta | Explicación Técnica |
| :--- | :--- | :--- |
| **Channel Name** | `EMERG FAM` | Identificación rápida en pantalla. |
| **Channel Mode** | `Digital` | Activa el chip de procesamiento de datos. |
| **Rx Frequency** | `462.56250` | Frecuencia de recepción (UHF Canal 1 Libre). |
| **Tx Frequency** | `462.56250` | Frecuencia de transmisión (Modo Simplex / Directo). |
| **Transmit Power**| `High` | Activa los 10W de potencia para máximo alcance. |
| **Color Code** | `1` | Filtro digital (ambos radios deben tener el mismo). |
| **Time Slot** | `Slot 1` | Canalización de tiempo nativa DMR. |
| **Contact Name** | `FAMILIA` | *Group Call* con ID `100` (crear previamente en Digital Contacts). |

### B. Canal de Respaldo: Analógico (`EMERG ANALOG`)
Esencial si el chip digital de un equipo falla por un golpe fuerte, o para interactuar con organismos de socorro que utilicen radios analógicos tradicionales (como el UV-5R).

| Parámetro en CPS | Configuración Exacta | Explicación Técnica |
| :--- | :--- | :--- |
| **Channel Name** | `EMERG ANALOG` | Identificación en pantalla. |
| **Channel Mode** | `Analog` | Modo tradicional de radio FM. |
| **Rx Frequency** | `462.56250` | Misma frecuencia del canal digital. |
| **Tx Frequency** | `462.56250` | Transmisión directa de radio a radio. |
| **Transmit Power**| `High` | Potencia máxima de salida. |
| **Ctccs / Dcs** | `None` / `Off` | Sin tonos analógicos para máxima compatibilidad en crisis. |

### C. Creación de la Zona Aislada de Seguridad
Para evitar que un familiar bajo estrés se confunda navegando entre frecuencias complejas de radioaficionados:
1. Crea una zona nueva en el CPS llamada **EMERGENCIA**.
2. Agrega como **Canal 1** a `EMERG FAM`.
3. Agrega como **Canal 2** a `EMERG ANALOG`.
4. Borra cualquier otro canal de esta zona específica.

---

## 2. Configuración Manual Directamente desde el Menú del Radio (VFO)

Si te encuentras en el campo sin una computadora y necesitas configurar el radio de inmediato para hablar en directo, sigue estos pasos utilizando el teclado físico del Baofeng DM-32 UV:

### Paso A: Pasar a Modo Frecuencia (VFO)
1. Enciende el radio.
2. Presiona la tecla **VFO/MR** (o mantén presionada la tecla de menú según la revisión de tu firmware) hasta que el radio deje de mostrar nombres de canales y muestre números de frecuencia grandes en pantalla.

### Paso B: Configuración del Canal Analógico Rápido (Recomendado por Teclado)
Programar DMR por teclado requiere ingresar IDs numéricos complejos, por lo que en una emergencia manual en el campo, la vía analógica es la más rápida y compatible:

1. Digita directamente en el teclado numérico la frecuencia: **462.56250**.
2. Presiona la tecla **MENU**.
3. Busca el parámetro de potencia (usualmente **TXP** o Menú 2) -> Presiona **MENU** -> Selecciona **HIGH** -> Presiona **MENU** para guardar.
4. Busca los parámetros de tonos (**R-CTCS** y **T-CTCS** o Menú 11 y 13) -> Asegúrate de que estén en **OFF** para que no bloqueen la recepción.
5. Si deseas guardarlo en una memoria vacía: Busca el menú **MEM-CH** -> Presiona **MENU** -> Selecciona un canal libre (ej. `001`) -> Presiona **MENU** para guardar la recepción. 
6. *(Nota: En algunos firmwares de Baofeng debes repetir el paso de MEM-CH transmitiendo en la misma frecuencia para fijar la frecuencia de TX).*

---

## 3. Frecuencias de Monitoreo de Emergencias Nacionales (Colombia)

**IMPORTANTE (REGLA DE ORO):** Estas frecuencias son estrictamente para **ESCUCHA Y MONITOREO**. No se debe transmitir en ellas a menos que la vida humana dependa de ello y no exista absolutamente ningún otro medio de comunicación (celular, internet, satelital) disponible.

Guarda estas frecuencias en una zona separada en tu CPS llamada `MONITOREO SOS`:

### A. Frecuencias VHF de Cobertura Nacional y Entidades de Socorro
* **141.650 MHz:** Frecuencia Nacional de Emergencias (Muy utilizada por Cruz Roja Colombiana y Defensa Civil en redes locales).
* **143.850 MHz:** Frecuencia de Coordinación de la Defensa Civil Colombiana.
* **142.150 MHz:** Red de Emergencias / Enlace Nacional de Radioaficionados (Segmento analógico).
* **145.000 MHz:** Frecuencia de Encuentro Nacional / Llamada en VHF (Radioaficionados).

### B. Segmentos Clave en el Departamento del Quindío (Locales)
* **147.240 MHz (+600 kHz, Tono 85.4):** Repetidora del Radio Club Calarcá / Red FRACOL Quindío (Es el nodo principal del departamento para reportes e interacción regional).
* **146.520 MHz:** Frecuencia nacional de encuentro en directo (Simplex VHF) entre radioaficionados. Excelente para monitorear si las repetidoras de las montañas colapsan.

---

## 4. Protocolo Familiar de Actuación en Crisis

1. **La Regla del Canal 1:** Ante un sismo o colapso de redes telefónicas, encender el radio y verificar que la pantalla dicte: **"Zona: EMERGENCIA - Canal: 1"**.
2. **Ciclo de Escucha Activa:** No satures la frecuencia transmitiendo constantemente. Transmite solo mensajes cortos y específicos:
   * *Ejemplo:* *"Aquí Radio A en casa, todos estamos bien, esperando reportes. Cambio"*.
3. **Mantenimiento Preventivo:** Realiza un simulacro familiar de audio el primer sábado de cada mes para verificar la autonomía real de las baterías y repasar el uso del equipo con la familia.