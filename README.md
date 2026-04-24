# 🏎️ Simulación de Carrera — POSIX Threads

> **Asignatura**: Sistemas Operativos — UAH  
> **Curso**: 2025-26  
> **Stack**: C · pthreads · Linux

## Descripción

Simulación de una carrera de coches mediante hilos POSIX en Linux.
Cada coche es representado por un hilo independiente que compite
con retardo aleatorio y registra su posición en una clasificación final compartida.

## Conceptos aplicados

- `pthread_create` / `pthread_join` / `pthread_exit`
- Exclusión mutua con `pthread_mutex_t`
- Protección de secciones críticas (clasificación compartida)
- Semillas aleatorias por hilo con `rand_r()` para evitar condiciones de carrera
- Compilación con `-lpthread`

## Problema de concurrencia resuelto

N hilos acceden concurrentemente a un array de clasificación global.
Sin mutex → race condition → orden de llegada incorrecto.
Con mutex → exclusión mutua garantizada → clasificación consistente.

## Compilación

```bash
gcc simula_car.c -o simula_car -lpthread
./simula_car
```

## Ejemplo de salida

Salida de Coche 0
Salida de Coche 3
...
Llegada de Coche 5    ← 1º
Llegada de Coche 2    ← 2º
...
CLASIFICACION FINAL:
1º → Coche 5
2º → Coche 2
