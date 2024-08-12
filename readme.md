# Verificación de Datos en Tarjeta RFID con Arduino y MFRC522

Este proyecto permite leer y verificar los datos almacenados en una tarjeta RFID utilizando el módulo MFRC522 y un Arduino. Si los datos leídos coinciden con los datos esperados, se emite un sonido de verificación a través de un buzzer. Si los datos no coinciden, se emite un sonido de denegado.

## Componentes Necesarios

- Arduino (por ejemplo, Uno, Nano, Mega)
- Módulo RFID RC522
- Tarjeta RFID o llavero RFID
- Buzzer pasivo
- Cables de conexión
- Protoboard (opcional)

## Diagrama de Conexión

- **VCC** del RC522 -> **3.3V** en Arduino
- **GND** del RC522 -> **GND** en Arduino
- **SDA/SS** del RC522 -> **Pin Digital 10** en Arduino
- **SCK** del RC522 -> **Pin Digital 13** en Arduino
- **MOSI** del RC522 -> **Pin Digital 11** en Arduino
- **MISO** del RC522 -> **Pin Digital 12** en Arduino
- **RST** del RC522 -> **Pin Digital 9** en Arduino
- **Pin Positivo del Buzzer** -> **Pin Digital 8** en Arduino
- **Pin Negativo del Buzzer** -> **GND** en Arduino

## Explicación del Código

Este código lee los datos almacenados en un bloque específico de una tarjeta RFID y los compara con un conjunto de datos esperados. Si los datos coinciden, se emite un sonido de verificación mediante un buzzer. Si no coinciden, se emite un sonido de denegado.

### Variables Clave

- `RST_PIN`: Pin de reset del módulo RFID RC522.
- `SS_PIN`: Pin de selección del esclavo (SDA) para el bus SPI.
- `BUZZER_PIN`: Pin que controla el buzzer pasivo.
- `expectedData[]`: Array que contiene los datos esperados para verificar con los datos leídos de la tarjeta RFID.

### Configuración

1. Iniciar la comunicación SPI y el módulo RFID.
2. Configurar el pin del buzzer como salida.

### Bucle Principal

1. Verificar si hay una nueva tarjeta presente.
2. Leer el UID de la tarjeta y mostrarlo en el Monitor Serial.
3. Autenticar y leer los datos del bloque especificado en la tarjeta.
4. Comparar los datos leídos con los datos esperados.
5. Emitir un sonido de verificación si los datos coinciden, o un sonido de denegado si no coinciden.
6. Poner la tarjeta en modo de suspensión para ahorrar energía.

## Cómo Usar

1. Conecta los componentes según el diagrama de conexión.
2. Sube el código a tu Arduino.
3. Acerca una tarjeta RFID al lector.
4. Observa el resultado en el Monitor Serial y escucha el sonido del buzzer para verificar si los datos de la tarjeta son correctos o no.

## Ejemplo de Salida

Si los datos coinciden:
```bash
UID de la tarjeta: 04 1A 7B 2C
```
(Sonido de verificación en el buzzer)

Si los datos no coinciden:
```bash
UID de la tarjeta: 04 1A 7B 2C
```
(Sonido de denegado en el buzzer)

## Notas

- Asegúrate de que el módulo RFID esté correctamente alimentado con 3.3V.
- El buzzer debe estar correctamente conectado al pin especificado para emitir los sonidos.
- Los datos esperados pueden ajustarse en el array `expectedData[]` para que coincidan con los datos que deseas verificar en la tarjeta.

## Licencia

Este proyecto es de código abierto y está disponible bajo la [Licencia MIT](LICENSE).
