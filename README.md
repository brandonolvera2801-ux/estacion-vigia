# Estación Vigía — Corte de proyecto (Fases 1–3)

Estructura de Datos · Ciclo 2026A · CUValles · UdeG

Programa en C con menú que integra las tres primeras fases del proyecto.

## Compilar y ejecutar

```bash
gcc -Wall -Wextra -std=c99 -o estacion_vigia estacion_vigia.c
./estacion_vigia
```

Compila sin advertencias con `-Wall -Wextra -pedantic`. En Windows (MinGW) el comando es el mismo y el ejecutable se llama `estacion_vigia.exe`.

## Estructuras implementadas

| Fase | Qué hace | Estructura / TAD |
|------|----------|------------------|
| 1 | Búfer de lecturas, promedio, máximo y mínimo | `Buffer`: arreglo dinámico (`malloc`, `realloc`, `free`) y recorrido con aritmética de punteros |
| 2 | Registro de alertas al cruzar un umbral (ALTA / BAJA); mostrar, buscar por tipo y eliminar | `ListaEventos`: lista enlazada simple con punteros a cabeza y cola; eliminación con puntero a puntero (`Evento **`) |
| 3 | Comandos al actuador en orden de llegada | `Cola` (FIFO) con nodos enlazados |
| 3 | Deshacer el último comando ejecutado | `Pila` (LIFO) con nodos enlazados |

## Menú

```
===== ESTACION VIGIA =====
1. Capturar lecturas (buffer dinamico)     <- Fase 1
2. Ver lecturas y estadisticas             <- Fase 1
3. Ver registro de eventos/alertas         <- Fase 2
4. Enviar comando al actuador (cola)       <- Fase 3
5. Ejecutar comandos pendientes            <- Fase 3
6. Deshacer ultimo comando (pila)          <- Fase 3
0. Salir (libera toda la memoria)
```

- **Opción 1:** permite cambiar los umbrales (por defecto ALTO > 80, BAJO < 20) y capturar lecturas en modo manual o aleatorio. Cada lectura que cruza un umbral genera un evento en la lista enlazada.
- **Opción 3:** submenú para mostrar todos los eventos, buscarlos por tipo, eliminar uno por id o eliminar todos los de un tipo.
- **Opción 4:** encola un comando (ventilador, válvula 0–100 % o alarma) sin ejecutarlo.
- **Opción 5:** ejecuta toda la cola en orden FIFO. Antes de aplicar cada comando se guarda el valor anterior en la pila.
- **Opción 6:** saca el tope de la pila y restaura el valor anterior del actuador.

## Manejo de memoria

- Toda la entrada se lee con `fgets` y se valida: letras, rangos inválidos o EOF no truenan el programa.
- Cada `malloc`/`realloc` se verifica contra `NULL`.
- Al salir (opción 0 o fin de entrada) se liberan el búfer, la lista de eventos, la cola y la pila.
- Verificado con AddressSanitizer/LeakSanitizer: sin fugas ni accesos inválidos.

## Equipo

| Integrante | Aporte |
|------------|--------|
| _Nombre 1_ | _Fase 1_ |
| _Nombre 2_ | _Fase 2_ |
| _Nombre 3_ | _Fase 3_ |
| _Nombre 4_ | _Integración, menú y documentación_ |

## Pendiente para el proyecto final

Recursión, ordenamiento, búsqueda binaria en tabla de calibración, reporte final y defensa.

## Pendiente para el proyecto final

Recursión, ordenamiento, búsqueda binaria en tabla de calibración, reporte final y defensa.
