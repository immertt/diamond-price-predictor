# 💎 Diamond Price Predictor

A Machine Learning-based diamond price prediction web application. Developed using Support Vector Machine (SVM) algorithm with a modern web interface.

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Technologies](#technologies)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Model Details](#model-details)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## 🎯 About the Project

This project uses the famous Diamonds dataset from Kaggle to predict diamond prices using machine learning. Users can input physical characteristics of a diamond (carat, cut, color, clarity, etc.) and get an estimated price prediction.

## ✨ Features

- 🤖 Trained Support Vector Machine (SVM) model
- 📊 Comprehensive EDA (Exploratory Data Analysis) and Feature Engineering
- 🎨 Modern and user-friendly web interface
- 📱 Responsive design (mobile-friendly)
- ⚡ Fast and reliable backend with FastAPI
- 🔄 Real-time price prediction
- ✅ Form validation and error handling
- 💾 Pickle serialization for model persistence

## 🛠 Technologies

### Backend
- **Python 3.x**
- **FastAPI** - Modern, fast web framework
- **Scikit-learn** - Machine learning library
- **Pandas** - Data manipulation and analysis
- **Pickle** - Model serialization
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation

### Frontend
- **HTML5**
- **CSS3** - Modern styling with gradients and animations
- **JavaScript (Vanilla)** - Async/await for API calls

### Machine Learning
- **Support Vector Machine (SVM)** - Main prediction algorithm
- **Label Encoding** - Categorical feature encoding
- **Standard Scaler** - Feature scaling

## 📦 Installation

### Prerequisites
```bash
Python 3.8 or higher
pip (Python package manager)
```

### Steps

1. **Clone the repository**
```bash
git clone https://github.com/immertt/diamond-price-predictor.git
cd diamond-price-predictor
```

2. **Create a virtual environment**
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install fastapi uvicorn pandas scikit-learn pydantic jinja2
```

4. **Ensure you have the required files**
- `app.py` - FastAPI application
- `diamond_model_complete.pkl` - Trained model and preprocessors
- `templates/index.html` - Frontend interface

## 🚀 Usage

1. **Start the FastAPI server**
```bash
uvicorn app:app --reload
```

2. **Open your browser**
Navigate to: `http://127.0.0.1:8000`

3. **Make predictions**
- Fill in the diamond characteristics:
  - **Carat**: Weight of the diamond (0.2 - 5.0)
  - **Cut**: Quality of the cut (Fair, Good, Very Good, Premium, Ideal)
  - **Color**: Diamond color grade (D to J, D being the best)
  - **Clarity**: How clear the diamond is (I1, SI2, SI1, VS2, VS1, VVS2, VVS1, IF)
  - **Depth**: Total depth percentage (43 - 79)
  - **Table**: Width of top of diamond relative to widest point (43 - 95)
  - **X**: Length in mm (0 - 11)
  - **Y**: Width in mm (0 - 60)
  - **Z**: Depth in mm (0 - 32)
- Click "Predict Price" button
- View the predicted price in USD

## 📊 Dataset

The project uses the **Diamonds dataset** from Kaggle, which contains:
- **53,940 diamonds** with their prices and attributes
- **10 features**: carat, cut, color, clarity, depth, table, price, x, y, z
- **Target variable**: price (in US dollars)

### Feature Descriptions

| Feature | Type | Description |
|---------|------|-------------|
| carat | float | Weight of the diamond |
| cut | categorical | Quality of the cut (Fair, Good, Very Good, Premium, Ideal) |
| color | categorical | Diamond color, from D (best) to J (worst) |
| clarity | categorical | How clear the diamond is (I1, SI2, SI1, VS2, VS1, VVS2, VVS1, IF) |
| depth | float | Total depth percentage = z / mean(x, y) |
| table | float | Width of top of diamond relative to widest point |
| price | int | Price in US dollars (target variable) |
| x | float | Length in mm |
| y | float | Width in mm |
| z | float | Depth in mm |

## 🤖 Model Details

### Preprocessing Pipeline
1. **Label Encoding** - Categorical features (cut, color, clarity) encoded to numerical values
2. **Standard Scaling** - All features scaled to have mean=0 and std=1
3. **Feature Engineering** - Comprehensive analysis performed before training

### Model Training
- **Algorithm**: Support Vector Machine (SVM)
- **Preprocessing**: Label Encoding + Standard Scaler
- **Serialization**: Model, encoders, and scaler saved using Pickle

### Model Performance
The model was evaluated using standard regression metrics during the EDA phase. All preprocessing components are saved and loaded for consistent predictions.
- **R² Score**: 0.9447
- **RMSE**: 926.2714
- **MAE**: 68.1153

## 🔌 API Endpoints

### GET `/`
Returns the main HTML interface.

**Response**: HTML page

---

### POST `/predict`
Predicts diamond price based on input features.

**Request Body**:
```json
{
  "carat": 1.04,
  "cut": "Very Good",
  "color": "D",
  "clarity": "SI1",
  "depth": 61.5,
  "table": 58,
  "x": 6.48,
  "y": 6.53,
  "z": 4
}
```

**Response**:
```json
{
  "predicted_price": 5515.44
}
```

**Status Codes**:
- `200 OK` - Successful prediction
- `422 Unprocessable Entity` - Invalid input data

## 📁 Project Structure

```
diamond-price-predictor/
│
├── app.py                          # FastAPI application
├── diamond_model_complete.pkl      # Trained model and preprocessors
├── diamonds.csv                    # Dataset (from Kaggle)
├── requirements.txt                # Python dependencies
├── README.md                       # Project documentation
│
├── templates/
│   └── index.html                  # Frontend interface

```

## 🧪 Testing

### Using Swagger UI
FastAPI provides interactive API documentation:
1. Navigate to `http://127.0.0.1:8000/docs`
2. Try out the `/predict` endpoint with sample data
3. View request/response formats

### Sample Test Data
```json
{
  "carat": 1.04,
  "cut": "Very Good",
  "color": "D",
  "clarity": "SI1",
  "depth": 61.5,
  "table": 58,
  "x": 6.48,
  "y": 6.53,
  "z": 4
}
```
Expected prediction: ~$5515.44

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License. 

## 👤 Author
**İbrahim Mert Akbaş**
- GitHub: [@immertt](https://github.com/immertt)
- LinkedIn: [İbrahim Mert Akbaş](https://www.linkedin.com/in/immertt/)

## 🙏 Acknowledgments

- Dataset provided by [Kaggle - Diamonds Dataset](https://www.kaggle.com/datasets/shivam2503/diamonds)
- FastAPI framework by Sebastián Ramírez
- Scikit-learn community

## 📞 Contact

For questions or feedback, please open an issue on GitHub or contact me directly.

---

**Made with ❤️ and Python**