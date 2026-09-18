# Lenguaje emsanblador emulador 8086 🖥️

## Estructura de un programa

Directiva `.MODEL` (o `MODEL`) es el tamaño maximo que el programa va ocupar y como va a repartir ese espacio.

### Tipos de `MODEL`
- `TINY` (Diminuto)
- `SMALL` (Pequeño)
- `MEDIUM` (Mediano)
- `COMPACT` (Compacto)
- `LARGE` o `HUGE` (Grande/Enorme)

El Segmento stack(pila) `.STACK` es un espacio de memoria temporal en la que la computadora usa para guadar cosas rapidamente y recuperarlas despues en orden inverso (LIFO).
Por defecto tiene asignado un tamaño de `1024 KB` o bien `1MB`.

El segmento de datos `.DATA` es el espacio de memoria reservado exclusivamente para definir y guardar todas las variables y constantes que un programa va a utilizar.

### ¿Qué puede guardar?
- Texto/Cadenas
- Numeros
- Espacios en blanco(Arreglos o buffers)

### ¿Cómo se definen?
Ejmplo: 
```asm
.DATA
    mensaje DB "Hola mundo$", 0
    edad DB 20
    total DW 1500
    buffer DB 50 DUP(?)
```

### Tipos de datos
|         Directiva          |        Tamaño           |                           Uso comun                                       |
|----------------------------|-------------------------|---------------------------------------------------------------------------|
|  `DB` (Define Byte)        |      8 bits (1Byte)     |      Cadenas de string o numeros pequeños `0-255` y/o `-128` a `127`      |
|  `DW` (Define Word)        |      16 bits (2 Bytes)  |      Numeros grandes mayores a `255`                                        |
|`DD` (Define Double word)   |      32 bits (4 Bytes)  |      Numero muchos mas grande mayores a `65,535`                          |

El segmento de codigo `.CODE` es la seccion donde se escribe todas las intucciones que la computadora debe ejecutar paso a paso.

### ¿Como se define?
```asm
.CODE 
    
    MAIN PROC

    ; AQUI ADENTRO SE PONDRAN LAS FUNCIONES Y PROCEDIMIENTOS
    
    MAIN ENDP

END MAIN
```

## Intrucciones o mnemónicos

Son las palabras que representan las operaciones que el procesador puede ejecutar.

### Transferencia de datos
|      Instruccion       |               ¿Qué hace?                 |
|------------------------|------------------------------------------|
|        `MOV`           |  Copia un valor de un lugar a otro       |
|        `LEA`           |  Carga la direccion de una variable      |
|        `PUSH`          |  Guarda un valor en la pila              |
|        `POP`           |  Saca un valor de la pila                |
|        `XCHG`          |  Intercambia el contenido de dos lugares |

### Aritméticas (Matematicas basicas)
|      Instruccion       |               ¿Qué hace?                         |
|------------------------|--------------------------------------------------|
|       `ADD`            |                Suma                              |
|       `SUB`            |                Resta                             |
|       `MUL`            |            Multiplica(Sin signo)                 |
|       `IMUL`           |     Multiplica(Con signo, numeros negativos)     |
|       `DIV`            |               Divide(Sin signo)                  |          
|       `IDIV`           |               Divide(Con signo)                  |

### Lógicas / bit a bit
|      Instrucción       |               ¿Qué hace?                          |
|------------------------|---------------------------------------------------|
|        `AND`           |                `Y` logico                         |
|        `OR`            |                `O` Logico                         | 
|        `XOR`           |                `O` Exclusivo                      |
|        `NOT`           |            Invierte todos los bits                |

### Comparación y saltos
|       Instrucción      |                ¿Qué hace?                         |
|------------------------|---------------------------------------------------|
|        `CMP`           |            Compara dos valores                    |
|        `JE`            |          Salta si es igual la comparacion         |
|        `JMP`           |        Salto incondicional (Siempre salta)        |
|        `JE/JZ`         |          Salta si es igual / si es cero           |
|        `JNE/JNZ`       |          Salta si NO es igual / no es cero        |
|        `JG / JL`       |          Salta si es mayor / menor                |
|        `JGE / JLE`     |      Salta si es mayor o igual / menor o igual    |

## Funciones de entrada/salida de texto

|     AH      |                ¿Qué hace?                                    |
|-------------|--------------------------------------------------------------|
|     `01H`   |             Leer un caracter                                 |
|     `02H`   |     Mostrar un caracter en pantalla se usa `DL`              |
|     `08H`   |     Leer caracter no muestra lo que se escribe               |
|     `09H`   |     Mostrar un texto completo en pantalla                    |
|     `0AH`   |   Lee varios caracteres hasta euq el usuario precione Enter  |
|     `0BH`   |        Verifica el estado del teclado                        |

## Tabla de codigo ASCII
![ASCII](https://examtimeassets.s3.amazonaws.com/uploads/node/image/98196337/desktop_05ccf296-bf5a-492b-86c8-9e49a908ded3.png)