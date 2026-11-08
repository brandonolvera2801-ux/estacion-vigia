Estacion Vigia — Corte de proyecto (Fases 1–3)

Estructura de Datos · Ciclo 2026A · CUValles · UdeG

Programa en C con menu que integra las tres primeras fases del proyecto.

Compilar y ejecutar
bash
gcc -Wall -Wextra -std=c99 -o estacion_vigia estacion_vigia.c
./estacion_vigia

Compila sin advertencias con -Wall -Wextra -pedantic. En Windows (MinGW) el comando es el mismo y el ejecutable se llama estacion_vigia.exe.

Estructuras implementadas
Fase	Que hace	Estructura / TAD
1	Bufer de lecturas, promedio, maximo y minimo	Buffer: arreglo dinamico (malloc, realloc, free) y recorrido con aritmetica de punteros
2	Registro de alertas al cruzar un umbral (ALTA / BAJA); mostrar, buscar por tipo y eliminar	ListaEventos: lista enlazada simple con punteros a cabeza y cola; eliminacion con puntero a puntero (Evento **)
3	Comandos al actuador en orden de llegada	Cola (FIFO) con nodos enlazados
3	Deshacer el ultimo comando ejecutado	Pila (LIFO) con nodos enlazados
Menu
===== ESTACION VIGIA =====
1. Capturar lecturas (buffer dinamico)     <- Fase 1
2. Ver lecturas y estadisticas             <- Fase 1
3. Ver registro de eventos/alertas         <- Fase 2
4. Enviar comando al actuador (cola)       <- Fase 3
5. Ejecutar comandos pendientes            <- Fase 3
6. Deshacer ultimo comando (pila)          <- Fase 3
0. Salir (libera toda la memoria)
Opcion 1: permite cambiar los umbrales (por defecto ALTO > 80, BAJO < 20) y capturar lecturas en modo manual o aleatorio. Cada lectura que cruza un umbral genera un evento en la lista enlazada.
Opcion 3: submenu para mostrar todos los eventos, buscarlos por tipo, eliminar uno por id o eliminar todos los de un tipo.
Opcion 4: encola un comando (ventilador, valvula 0–100 % o alarma) sin ejecutarlo.
Opcion 5: ejecuta toda la cola en orden FIFO. Antes de aplicar cada comando se guarda el valor anterior en la pila.
Opcion 6: saca el tope de la pila y restaura el valor anterior del actuador.
Manejo de memoria
Toda la entrada se lee con fgets y se valida: letras, rangos invalidos o EOF no truenan el programa.
Cada malloc/realloc se verifica contra NULL.
Al salir (opcion 0 o fin de entrada) se liberan el bufer, la lista de eventos, la cola y la pila.
Verificado con AddressSanitizer/LeakSanitizer: sin fugas ni accesos invalidos.
Equipo
Integrante	Aporte
Nombre 1	Fase 1
Nombre 2	Fase 2
Nombre 3	Fase 3
Nombre 4	Integracion, menu y documentacion
Pendiente para el proyecto final

Recursion, ordenamiento, busqueda binaria en tabla de calibracion, reporte final y defensa.

## Pendiente para el proyecto final

Recursión, ordenamiento, búsqueda binaria en tabla de calibración, reporte final y defensa.
