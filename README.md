# Subneting

### IP = Internet Protocol
### IPV4 = 32 bits = Decimal = 4 octetos = 0 - 255 --> 256 = Binario 0 - 1

## Binario
---
### IP privada = 192.168.100.120 cada octeto equivale a 8 bits

### Ejemplo

| Dirección IP | Bits |
| ------------ | ---- |
| 192          | 8    |
| 168          | 8    |
| 100          | 8    |
| 120          | 8    |
| **Total**    | **32** bits |

### Vamos a transformar en binario la siguiente IP privada para ello tendremos nuestra tabla de apoyo.

| Potencia | Valor |
| -------- | ----- |
| 2^7      | 128   |
| 2^6      | 64    |
| 2^5      | 32    |
| 2^4      | 16    |
| 2^3      | 8     |
| 2^2      | 4     |
| 2^1      | 2     |
| 2^0      | 1     |

### 192.168.100.10

| Decimal | Binario    |
| ------- | ---------- |
| 192     | 11000000   |
| 168     | 10101000   |
| 100     | 01100100   |
| 10      | 00001010   |

## Direcciónamiento IP con Clase RFC 790
---

| Clase A   |                                             |
| --------- | ------------------------------------------- |
| Características: |                                   |
| Rango:    | 0 - 127                                   |
| Máscara:  | /8 o 255.0.0.0                            |
| Host:    | 2^24 = 16,777,216                     |
| Exclusiones:  |                                      |
| 0.0.0.0/8       | Follgroup (averiguar)                     |
| 10.0.0.0/8      | Direccionamiento privado                   |
| 127.0.0.0/8     | Testing looback                            |

| Clase B   |                                             |
| --------- | ------------------------------------------- |
| Características: |                                   |
| Rango:    | 128 - 191                                   |
| Máscara:  | /16 o 255.255.0.0                            |
| Host:    | 2^16 = 65,536                     |
| Exclusiones:  |                                      |
| 172.16.0.0/12       | APIPA RFC 3927                     |
| 169.254.0.0/16      | APIPA RFC 3927                   |

| Clase C   |                                             |
| --------- | ------------------------------------------- |
| Características: |                                   |
| Rango:    | 192 - 223                                   |
| Máscara:  | /24 o 255.255.255.0                            |
| Host:    | 2^8 = 256                     |
| Exclusiones:  |                                      |
| 192.168.0.0/16     |


| Clase D   |                                         |
| --------- | --------------------------------------- |
| Características: |                             |
| Rango:    | 224 - 239                              |
| Máscara:  | La máscara de subred para la Clase D no se utiliza típicamente, ya que no se realiza una segmentación en subred en el contexto del direccionamiento multicast. |
| Hosts:    | -                                      |
| Exclusiones:  |                                    |
| No hay exclusiones específicas en la Clase D |                                         |

| Clase E   |                                         |
| --------- | --------------------------------------- |
| Características: |                             |
| Rango:    | 240 - 255                              |
| Máscara:  | La máscara de subred para la Clase E no se utiliza típicamente, ya que no se realiza una segmentación en subred en el contexto del direccionamiento experimental. |
| Hosts:    | -                                      |
| Exclusiones:  |                                    |
| No hay exclusiones específicas en la Clase E |                                         |

## Subneteo Clase C
---

| Cantidad de Host totales | Número de subredes | Mascara | Mascara          | Formula       |
| ------------------------ | ------------------ | ------- | ---------------- | ------------- |
| 128                      | 2                  | 25      | 255.255.255.128  | 256/2-2       |
| 64                       | 4                  | 26      | 255.255.255.192  | 256/4-2       |
| 32                       | 8                  | 27      | 255.255.255.224  | 256/8-2       |
| 16                       | 16                 | 28      | 255.255.255.240  | 256/16-2      |
| 8                        | 32                 | 29      | 255.255.255.248  | 256/32-2      |
| 4                        | 64                 | 30      | 255.255.255.252  | 256/64-2      |

### Vamos a realizar un ejemplo con la siguiente ip 192.168.0.0
### Nos piden CHT: 8 Subred: 10 "CHT me refiero a cantitdad de host totales"

| CHT: 8 | Subred: 10 | Formula                   | Comentario                          |
| ------- | ----------- | ------------------------ | ----------------------------------- |
|         |             | IP Sub = CHT * #Subred   | Con esta fórmula podemos encontrar el IP de esta subred |
|         |             |                          |                                     |
| IP Subred: | 192.168.0.80 | 8 * 10 = 80          |                                     |
| Broadcast: | 192.168.0.87 | IP Sub + (CHT-1) = Broadcast | La siguiente fórmula es para el Broadcast |
| Gateway: | 192.168.0.81 or 192.168.0.86 | 80 + (8-1) = 87 |                                     |
| Mascara: | 255.255.255.248 |                      |                                     |

### Ejercicios
### 1.- ¿ Cual es el IP de subred para los siguientes  requerimientos. (IP base: 192.168.0.0) ?
### CHT: 15        Subred: #4

| CHT      | Subred  | Formula                  | Resultado       |
| -------- | ------- | ------------------------ | --------------- |
| 15       | 4       | IP Sub = CHT * #Subred   | 15 * 4 = 60     |
|          |         |                          |                 |
| Subred:  |         |                          | 192.168.0.60    |

### Rspt: 192.168.0.60

### 2.- ¿ Cual es el IP de subred para los siguientes  requerimientos. (IP base: 192.168.0.0) ?
### CHT: 4        Subred: #44

| CHT      | Subred  | Formula                  | Resultado       |
| -------- | ------- | ------------------------ | --------------- |
| 4       | 44       | IP Sub = CHT * #Subred   | 4 * 44 = 176     |
|          |         |                          |                 |
| Subred:  |         |                          | 192.168.0.176    |

### Rspt: 192.168.0.176

### 3.- ¿ Cual es el broadcast para los siguientes  requerimientos (IP base: 192.168.0.0) ?
### CHT: 32        Subred: #4

| CHT      | Subred  | Formula                  | Resultado       |
| -------- | ------- | ------------------------ | --------------- |
| 32       | 4       | IP Sub = CHT * #Subred   | 32 * 4 = 128     |
|          |         |                          |                 |
| Subred:  |         |                          | 192.168.0.128    |

| Broadcast  |             |                            |
| ---------- | ----------- | -------------------------- |
| IPSub      | CHT - 1     | Broadcast = IPSub + (CHT - 1) |
| ---------- | ----------- | -------------------------- |
| 128        | 31          | 128 + 31 = 159             |

### Rspt: 192.168.0.159

## Subneteo Clase B
---

### Vamos a comenzar por los que tienen más de 256 hosts

### Tenemos la tabla que nos ayudara

### Ejemplo 1 
### CHT: 400	Subred: 4 IP 172.16.0.0

| Formula                               | Comentarios                                 |
| ------------------------------------- | ------------------------------------------- |
| IP Sub = (CHT / 256) x #Subred         |                                             |
| IP Sub = (512 / 256) x 4 = 8          | Elegí 512 que es el número que supera a 400 hosts |
| Broadcast                             |                                             |
| Broadcast = 8 + (2 - 1) = 9           | Bajé el resultado de la división de 512/256 = 2 |
|                                       |                                             |
|                                       |  Verificamos la tabla 512 es una máscara de 23 bits                      |


| Resultado        |                                   |
| ---------------- | --------------------------------- |
| IP Sub           | 172.16.8.0                        |
| Boad             | 172.16.9.255                      |
| Gate             | 172.16.8.1 or 172.16.9.254        |
| Mask             | 255.255.254.0                     |

### Ejemplo 2
### CHT: 8192	Subred: 5 IP 172.16.0.0

| Formula                               | Resultado     |               |
| ------------------------------------- | --------------| ------------- |
| IP Sub = (CHT / 256) x #Subred        |   IP Sub      |   172.16.160.0  |
| IP Sub = (8192 / 256) x 5 = 160       |   Boad        |   172.16.191.255 |
| Broadcast                             |   Gate        |   172.16.161.0 o 172.16.191.254 |
| Broadcast = 160 + (32 - 1) = 191      |   Mask        |   255.255.224.0   |

### Ahora vamos a ver los que tienen igual o menor de 256 hosts
### Ejemplo 1

### CHT 64 Subred: 10 IP 172.16.0.0

| Formula                     | Comentarios                |
| ------------------------    | -------------------------- |
| IP Sub = ( 256 / 64 ) = 4   | IP Sub = ( 256 / CHT )   |
| 10 / 4 = 2.5                | Subred / IP Sub, tomamos el número entero: 172.16.2.0                 |
| 4 x 2 = 8                | Tomamos 4 (resultado de la operación anterior) x 2 que fue el resultado  |
| 10 - 8 = 2               | Subred 10 - 8 que fue el resultado 2 redes pendientes  |
| 2 x 64 = 128             | 2 x 64 (cantidad de hosts)  |

| Formula                          | Comentarios                |
| -------------------------------- | -------------------------- |
| Broadcast = Ip Sub + ( CHT - 1 ) |                            |
| 128 + ( 64 - 1 ) = 191           | Broadcast 191              |

| Resultado        |                                     |
| ---------------- | ----------------------------------- |
| IP Sub           | 172.16.2.128                        |
| Boad             | 172.16.2.191                        |
| Gate             | 172.16.2.129 or 172.16.2.190        |
| Mask             | 255.255.255.192                     |

### Ejemplo 2
### CHT 16 Subred: 172.16.0.0

| Formula IP Sub              |
| --------------------------- |
| IP Sub = ( 256 / 16 ) = 16  |
| 100 / 16 = 6.25             |
| 16 x 6 = 96                 |
| 100 - 96 = 4                |
| 4 x 16 = 64                 |

| Formula  Broadcast               |
| -------------------------------- |
| Broadcast = Ip Sub + ( CHT - 1 ) |
| 64 + ( 16 - 1 ) = 79           |

| Resultado        |                                     |
| ---------------- | ----------------------------------- |
| IP Sub           | 172.16.6.64                        |
| Boad             | 172.16.6.79                        |
| Gate             | 172.16.6.65 or 172.16.6.78        |
| Mask             | 255.255.255.240                     |

### Ejemplo 3
### CHT 4 Subred 7777 IP 172.16.0.0

| Formula IP Sub              |
| --------------------------- |
| IP Sub = ( 256 / 4 ) = 64   |
| 7777 / 64 = 121.5           |
| 64 x 121 = 7744             |
| 7777 - 7744 = 33            |
| 33 x 4 = 132                |

| Formula  Broadcast               |
| -------------------------------- |
| Broadcast = Ip Sub + ( CHT - 1 ) |
| 132 + ( 4 - 1 ) = 135           |

| Resultado        |                                     |
| ---------------- | ----------------------------------- |
| IP Sub           | 172.16.121.132                        |
| Boad             | 172.16.121.135                        |
| Gate             | 172.16.121.133 or 172.16.121.134        |
| Mask             | 255.255.255.252                     |

