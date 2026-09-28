# utec-shell · init_files_variables_and_expansions

Colección de scripts en Bash sobre **alias, variables de entorno, `PATH` y expansiones aritméticas** del shell.

## Requisitos

- Linux (probado en Ubuntu)
- Bash
- Permisos de ejecución sobre los scripts:

```bash
chmod +x *
```

## Uso

La mayoría de los scripts se ejecutan directamente:

```bash
./1-hello_you
```

Los que modifican el entorno de tu shell actual (alias, `PATH`, variables) deben **cargarse con `source`**. Si se ejecutan normalmente, corren en un subshell y el cambio se pierde al terminar:

```bash
source ./0-alias
. ./2-path
```

## Scripts

| Archivo | Descripción | Uso |
|---|---|---|
| `0-alias` | Crea el alias `ls` con valor `rm -f *` | `source` |
| `1-hello_you` | Imprime `hello <usuario actual>` | ejecutar |
| `2-path` | Agrega `/action` al final del `PATH` | `source` |
| `3-paths` | Cuenta los directorios del `PATH` | `source` o ejecutar |
| `4-global_variables` | Lista las variables de entorno | `source` o ejecutar |
| `5-local_variables` | Lista variables locales, de entorno y funciones | `source` o ejecutar |
| `6-create_local_variable` | Crea la variable local `BEST=School` | `source` |
| `7-create_global_variable` | Crea la variable global `BEST=School` | `source` |
| `8-true_knowledge` | Suma 128 a `$TRUEKNOWLEDGE` | ejecutar |
| `9-divide_and_rule` | Divide `$POWER` entre `$DIVIDE` | ejecutar |
| `10-love_exponent_breath` | Calcula `$BREATH` elevado a `$LOVE` | ejecutar |
| `11-binary_to_decimal` | Convierte `$BINARY` (base 2) a base 10 | ejecutar |
| `12-combinations` | Imprime todas las combinaciones de dos letras (`aa`–`zz`), excepto `oo` | ejecutar |
| `13-print_float` | Imprime `$NUM` con dos decimales | ejecutar |
| `14-decimal_to_hexadecimal` | Convierte `$DECIMAL` (base 10) a base 16 | ejecutar |

## Ejemplos

```bash
$ export TRUEKNOWLEDGE=1209
$ ./8-true_knowledge
1337

$ export POWER=42784 DIVIDE=32
$ ./9-divide_and_rule
1337

$ export BREATH=4 LOVE=3
$ ./10-love_exponent_breath
64

$ export BINARY=10100111001
$ ./11-binary_to_decimal
1337

$ export NUM=3.14159265359
$ ./13-print_float
3.14

$ export DECIMAL=1337
$ ./14-decimal_to_hexadecimal
539

$ ./12-combinations | wc -l
675
```

## Notas

- `0-alias` define un alias que **borra archivos** al escribir `ls`. Probalo solo en un directorio temporal (por ejemplo `/tmp/0x03`). Para revertirlo: `unalias ls`. Con `\ls` se ignora el alias.
- `3-paths` cuenta solo las entradas no vacías del `PATH`.
- `12-combinations` cumple el límite de 64 caracteres por archivo.
- `14-decimal_to_hexadecimal` imprime en minúsculas (`f`, no `F`).
