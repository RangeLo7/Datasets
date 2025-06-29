This File was Generated Randomly using the following python code:

import pandas as pd
import numpy as np
import random

# Definición de listas de posibles valores y mapeos extendidos
modelos_info = {
    'Civic': {'marca': 'Honda', 'segmento': 'Compacto', 'es_electrico_prob': 0.05},
    'Corolla': {'marca': 'Toyota', 'segmento': 'Compacto', 'es_electrico_prob': 0.1},
    'Golf': {'marca': 'Volkswagen', 'segmento': 'Compacto', 'es_electrico_prob': 0.15},
    'Focus': {'marca': 'Ford', 'segmento': 'Compacto', 'es_electrico_prob': 0.05},
    'Model 3': {'marca': 'Tesla', 'segmento': 'Sedan', 'es_electrico_prob': 1.0}, # Siempre eléctrico
    'Fusion': {'marca': 'Ford', 'segmento': 'Sedan', 'es_electrico_prob': 0.0},
    'CR-V': {'marca': 'Honda', 'segmento': 'SUV Compacto', 'es_electrico_prob': 0.1},
    'RAV4': {'marca': 'Toyota', 'segmento': 'SUV Compacto', 'es_electrico_prob': 0.15},
    'CX-5': {'marca': 'Mazda', 'segmento': 'SUV Compacto', 'es_electrico_prob': 0.0},
    'Q5': {'marca': 'Audi', 'segmento': 'SUV Premium', 'es_electrico_prob': 0.2},
    '3 Series': {'marca': 'BMW', 'segmento': 'Sedan Premium', 'es_electrico_prob': 0.1},
    'C-Class': {'marca': 'Mercedes-Benz', 'segmento': 'Sedan Premium', 'es_electrico_prob': 0.1},
    'Mustang': {'marca': 'Ford', 'segmento': 'Deportivo', 'es_electrico_prob': 0.0},
    'Camry': {'marca': 'Toyota', 'segmento': 'Sedan Mediano', 'es_electrico_prob': 0.05},
    'Tucson': {'marca': 'Hyundai', 'segmento': 'SUV Compacto', 'es_electrico_prob': 0.1},
    'Kona': {'marca': 'Hyundai', 'segmento': 'SUV Subcompacto', 'es_electrico_prob': 0.3},
    'Cherokee': {'marca': 'Jeep', 'segmento': 'SUV Mediano', 'es_electrico_prob': 0.0},
    'Silverado': {'marca': 'Chevrolet', 'segmento': 'Pickup Grande', 'es_electrico_prob': 0.0},
    'F-150': {'marca': 'Ford', 'segmento': 'Pickup Grande', 'es_electrico_prob': 0.05},
    'Sprinter': {'marca': 'Mercedes-Benz', 'segmento': 'Comercial', 'es_electrico_prob': 0.1}
}

paises_venta = [
    'México', 'Estados Unidos', 'Canadá', 'Brasil', 'Argentina', # América
    'Alemania', 'Francia', 'Reino Unido', 'España', 'Italia',   # Europa
    'China', 'Japón', 'Corea del Sur', 'India', 'Australia',     # Asia/Oceanía
    'Sudáfrica'                                                  # África
]

# Mapeo de países a continentes
mapa_continentes = {
    'México': 'América',
    'Estados Unidos': 'América',
    'Canadá': 'América',
    'Brasil': 'América',
    'Argentina': 'América',
    'Alemania': 'Europa',
    'Francia': 'Europa',
    'Reino Unido': 'Europa',
    'España': 'Europa',
    'Italia': 'Europa',
    'China': 'Asia',
    'Japón': 'Asia',
    'Corea del Sur': 'Asia',
    'India': 'Asia',
    'Australia': 'Oceanía',
    'Sudáfrica': 'África'
}

# Número de observaciones deseado
num_observaciones = 10000

# Listas para almacenar los datos generados
modelos_generados = []
anos_generados = []
ids_modelo_generados = []
paises_generados = []
unidades_vendidas_generadas = []
total_ventas_generadas = []
es_electrico_generado = []
tipo_transmision_generado = []
continente_generado = []
marca_generado = []
segmento_generado = []
es_nuevo_generado = []

# Generar datos aleatorios
for _ in range(num_observaciones):
    modelo = random.choice(list(modelos_info.keys()))
    info_modelo = modelos_info[modelo]
    pais = random.choice(paises_venta)
    ano = random.randint(2015, 2024)
    unidades = random.randint(50, 5000)
    total_ventas = round(random.uniform(1500000, 250000000), 2)

    modelos_generados.append(modelo)
    anos_generados.append(ano)
    ids_modelo_generados.append(f'{random.choice("ABCDEFGHIJKLMNOPQRSTUVWXYZ")}{random.randint(1000, 9999)}-{random.randint(10, 99)}')
    paises_generados.append(pais)
    unidades_vendidas_generadas.append(unidades)
    total_ventas_generadas.append(total_ventas)

    # Lógica para Es_Electrico basada en la probabilidad del modelo
    es_electrico_generado.append('Sí' if random.random() < info_modelo['es_electrico_prob'] else 'No')

    tipo_transmision_generado.append(random.choice(['Automático', 'Manual']))
    continente_generado.append(mapa_continentes[pais])
    marca_generado.append(info_modelo['marca'])
    segmento_generado.append(info_modelo['segmento'])

    # Variable 'Es_Nuevo': Alta probabilidad de ser nuevo si el año es reciente (2023-2024)
    es_nuevo_generado.append('Sí' if ano >= 2023 and random.random() < 0.9 else 'No')


# Crear el DataFrame de Pandas
df = pd.DataFrame({
    'Modelo_Auto': modelos_generados,
    'Ano_Auto': anos_generados,
    'ID_Modelo': ids_modelo_generados,
    'Pais_Venta': paises_generados,
    'Continente_Venta': continente_generado, # Añadido aquí para orden
    'Marca_Auto': marca_generado,            # Nueva variable
    'Segmento_Auto': segmento_generado,      # Nueva variable
    'Es_Electrico': es_electrico_generado,
    'Tipo_Transmision': tipo_transmision_generado,
    'Es_Nuevo': es_nuevo_generado,           # Nueva variable
    'Unidades_Vendidas': unidades_vendidas_generadas,
    'Total_Ventas': total_ventas_generadas
})
