
![Logo_compuesto_vof_2025](https://github.com/user-attachments/assets/df7db686-cfb0-4b47-a125-8cc28e402332)

# 🌸 API de Predicción de la Flor de Iris

Esta API creada con Flask utiliza algoritmos de machine learning para predecir el tipo de iris basándose en las características de sus pétalos y sépalos. 

## 🛠️ Modelos Utilizados

Los siguientes modelos se han implementado:

- **Regresión Logística**: `joblib.load("./models/model_logistic.h5")`
- **Random Forest**: `joblib.load("./models/model_forest.h5")`
- **SVM**: `joblib.load("./models/model_svm.h5")`
- **Árbol de Decisión**: `joblib.load("./models/model_tree.h5")`

## 🌼 Clases de Iris

python
clases_iris = {
    0: "setosa",
    1: "versicolor",
    2: "virginica"
}

# 🚀 Endpoints

## 📊 Predicción con Regresión Logística

@app.route('/predict/logistic', methods=['POST'])
def predict_logistic():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['logistic'], features)
    return jsonify({'modelo': 'Logistic Regression', 'prediccion': prediction, 'clase': label})

## 🌲 Predicción con Random Forest

@app.route('/predict/randomforest', methods=['POST'])
def predict_randomforest():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['randomforest'], features)
    return jsonify({'modelo': 'Random Forest', 'prediccion': prediction, 'clase': label})

## 🧠 Predicción con SVM

@app.route('/predict/svm', methods=['POST'])
def predict_svm():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['svm'], features)
    return jsonify({'modelo': 'SVM', 'prediccion': prediction, 'clase': label})

## 🌳 Predicción con Árbol de Decisión

@app.route('/predict/tree_decision', methods=['POST'])
def predict_tree():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['tree'], features)
    return jsonify({'modelo': 'Decision Tree', 'prediccion': prediction, 'clase': label})

# 📜 Arquitectura de la API REST
REST (Representational State Transfer) es un estilo arquitectónico para diseñar aplicaciones en red. Se basa en un protocolo de comunicación sin estado, cliente-servidor y cacheable: el HTTP. Las aplicaciones RESTful utilizan peticiones HTTP para realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre recursos.

Principios Clave de la Arquitectura REST
Interfaz Uniforme:

Simplifica y desacopla la arquitectura, permitiendo que cada parte evolucione de manera independiente.
Principios:
Basado en Recursos: Los recursos son identificados por URIs (Identificadores Uniformes de Recursos).
Manipulación de Recursos a Través de Representaciones: Los clientes tienen suficiente información para modificar o eliminar recursos en el servidor.
Mensajes Autodescriptivos: Cada mensaje contiene suficiente información para describir cómo procesarlo.
Hipermedia como Motor del Estado de la Aplicación (HATEOAS): Los clientes interactúan con la aplicación exclusivamente a través de hipermedia proporcionada dinámicamente por los servidores de la aplicación.
Sin Estado:

Cada solicitud del cliente al servidor debe contener toda la información necesaria para entender y procesar la solicitud.
Cacheable:

Las respuestas deben definirse como cacheables o no cacheables. Si una respuesta es cacheable, el cliente puede reutilizar los datos de respuesta para solicitudes posteriores.
Cliente-Servidor:

La arquitectura cliente-servidor separa las preocupaciones de la interfaz de usuario de las preocupaciones de almacenamiento de datos.
Sistema en Capas:

Permite que una aplicación esté compuesta por capas jerárquicas, restringiendo el comportamiento de los componentes.
Código a Demanda (Opcional):

Los servidores pueden extender la funcionalidad del cliente al transferir código ejecutable. Esta restricción es opcional y no se utiliza comúnmente.
Métodos HTTP en REST
Las APIs RESTful utilizan comúnmente métodos HTTP para realizar operaciones sobre recursos:

GET: Recuperar un recurso.
POST: Crear un nuevo recurso.
PUT: Actualizar un recurso existente.
DELETE: Eliminar un recurso.

# 📬 Uso

Puedes realizar peticiones POST a los endpoints especificados utilizando Postman para obtener la predicción del tipo de iris basado en las características que proporciones.
