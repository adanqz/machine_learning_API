# 🌸 API de Predicción de la Flor de Iris

Esta API utiliza algoritmos de machine learning para predecir el tipo de iris basándose en las características de sus pétalos y sépalos. 

## 🛠️ Modelos Utilizados

Los siguientes modelos se han implementado:

- **Regresión Logística**: `joblib.load("./models/model_logistic.h5")`
- **Random Forest**: `joblib.load("./models/model_forest.h5")`
- **SVM**: `joblib.load("./models/model_svm.h5")`
- **Árbol de Decisión**: `joblib.load("./models/model_tree.h5")`

### 🌼 Clases de Iris

python
clases_iris = {
    0: "setosa",
    1: "versicolor",
    2: "virginica"
}

#🚀 Endpoints

##🏠 Home

@app.route('/', methods=['GET'])
def home():
    return """
    <h1>API de Predicción de la Flor de Iris</h1>
    <p>Utiliza los endpoints para predecir la clase de una flor de iris basándote en sus características.</p>
    """
    
##📊 Predicción con Regresión Logística

@app.route('/predict/logistic', methods=['POST'])
def predict_logistic():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['logistic'], features)
    return jsonify({'modelo': 'Logistic Regression', 'prediccion': prediction, 'clase': label})

##🌲 Predicción con Random Forest

@app.route('/predict/randomforest', methods=['POST'])
def predict_randomforest():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['randomforest'], features)
    return jsonify({'modelo': 'Random Forest', 'prediccion': prediction, 'clase': label})

##🧠 Predicción con SVM

@app.route('/predict/svm', methods=['POST'])
def predict_svm():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['svm'], features)
    return jsonify({'modelo': 'SVM', 'prediccion': prediction, 'clase': label})

##🌳 Predicción con Árbol de Decisión

@app.route('/predict/tree_decision', methods=['POST'])
def predict_tree():
    features = obtener_features(request)
    if features is None:
        return jsonify({'error': 'Parámetros incorrectos'}), 400
    prediction, label = hacer_prediccion(modelos['tree'], features)
    return jsonify({'modelo': 'Decision Tree', 'prediccion': prediction, 'clase': label})
  
