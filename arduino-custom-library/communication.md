---
description: Library สำหรับควบคุม I2C/TWI, LCD Display, etc.
cover: >-
  https://images.unsplash.com/photo-1603732551658-5fabbafa84eb?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxhcmR1aW5vJTIwY29tbXVuaWNhdGlvbnxlbnwwfHx8fDE3MTEzOTM3MDl8MA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# 📡 Communication

### iEE\_I2C.h

[https://github.com/Jiranuwat-k/iEEI2C](https://github.com/Jiranuwat-k/iEEI2Clcd)

```cpp
// Scan I2C Devices Example
#include "iEE_I2C.h"
// iEE_I2C i2c;
void ScanI2CDevices(void) {
  char sbuf[32];
  int n_devices = 0;
  uint8_t addr = 0;
  for(; addr <= 128; addr++){
    uint8_t result = i2c.StartTransmission(addr << 1);
    i2c.EndTransmission();
    if (result) { // error
      delay(10);
    } else {
      n_devices++;
      Serial.print("0x");
      Serial.println(addr,HEX);
    }
  }
  Serial.print("Devices found: ");
  Serial.println(n_devices);
  Serial.print("-------------------------------\n\n");
}
void setup(){
  Serial.begin(115200);
  i2c.begin();
}

void loop(){
  Serial.print("I2C Scan....\n");
  ScanI2CDevices();
  delay(1000);
}
```

### iEE\_I2Clcd.h

[https://github.com/Jiranuwat-k/iEEI2Clcd](https://github.com/Jiranuwat-k/iEEI2Clcd)    Required : iEE\_I2C.h

