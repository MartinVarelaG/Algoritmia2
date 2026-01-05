# Actividad 2 — Planificación multiobjetivo de rutas de drones

En la actividad implemento 3 algoritmos para planificar una ruta tipo circuito Hamiltoniano minimizando:

- Distancia total
- Riesgo total por las zonas no.fly
- Número de recargas necesarias

En las instancias JSON se registran los nodos y los polígonos no-fly

## Estructura

- `exact_bb/` → backtracking / branch-and-bound.
- `geo_heuristic/` → heurística geométrica (greedy + 2-opt).
- `metaheuristic/` → simulated annealing (SA) multiarranque.
- `common/` → carga de instancias, evaluación de rutas, Pareto, geometría y plotting.
- `datasets/` → instancias `.json` (N=10,15,20,25).
- `scripts/` → generación de instancias y experimentos.
- `results/` → salidas y gráficas.

## Requisitos

- Python 3
- `matplotlib`

Instalación rápida:

  sudo apt update
	sudo apt install -y python3-venv
	python3 -m venv .venv
	source .venv/bin/activate
	python -m pip install --upgrade pip
	pip install -r requirements.txt

## Ejecutar un algoritmo en una instancia

Con Makefile:

Ejecuta 5 réplicas por instancia y algoritmo, y guarda los datos de las medias en el csv y genera gráficas en png en base a los resultados:

make experimento

Se guardan:
- `results/metricas.csv`
- `results/tiempo_vs_n.png`
- `results/hypervolumen.png`
- `results/diversidad.png`
- `results/pareto_inst_25.png`

## Formato de instancia JSON

Mira `datasets/inst_10.json` como plantilla. Los campos importantes son:
- `nodes`: coordenadas (x,y) y tipo
- `recharge_stations`: ids donde se puede recargar
- `battery_capacity`: capacidad (en las mismas unidades que el consumo)
- `polygons`: lista de polígonos no-fly

Autor: (Martín Varela García


> Nota: también existen aliases en inglés (`make run`, `make experiment`, `make gen`) por compatibilidad, pero en la entrega uso los nombres en castellano.
