# STREAMLIT APP - INSTALLATION & DEPLOYMENT GUIDE

## 📋 Prerequisites
- Python 3.8 or higher
- pip (Python package manager)

## 🔧 Installation Steps

### 1. Install Required Packages
```bash
pip install -r requirements.txt
```

Or install individually:
```bash
pip install streamlit pandas numpy scikit-learn folium streamlit-folium matplotlib seaborn plotly
```

### 2. Verify Installation
```bash
streamlit --version
```

## 🚀 Running the App

### Local Development
```bash
streamlit run carpool_streamlit_app.py
```

The app will open at: `http://localhost:8501`

### Deploy to Streamlit Cloud (Recommended)

1. Push your code to GitHub
2. Go to https://share.streamlit.io
3. Click "New app"
4. Select your GitHub repo, branch, and file
5. Click "Deploy"

### Deploy to Heroku
```bash
git init
heroku login
heroku create your-app-name
git push heroku main
```

### Deploy to AWS/Azure/GCP
Use their respective container deployment services.

## 📁 Required Files for Deployment
- `carpool_streamlit_app.py` - Main Streamlit application
- `car-data.csv` - Dataset
- `carpool_model.pkl` - Trained ML model
- `encoders.pkl` - Label encoders
- `location_coordinates.pkl` - Location coordinates
- `requirements.txt` - Python dependencies

## ⚙️ App Features

### 1. Search Interface
- Select pickup and drop locations
- Choose travel date
- Automatic distance calculation

### 2. Interactive Map
- Folium map showing both locations
- Blue line connecting pickup to destination
- Markers for both locations
- Distance display

### 3. Fare Estimation
- Base fare calculation
- Distance-based charges
- Fuel type multipliers
- Passenger sharing discounts
- Peak hour surcharges

### 4. Vehicle Display
- Shows available cars on the route
- Car name, seats, fuel type, age
- Estimated fare per vehicle

### 5. Pricing Customization
- Adjust fuel type
- Select number of passengers
- Enable/disable peak hour pricing
- Real-time fare recalculation

## 🎨 UI Elements

The dashboard includes:
- **Header:** Gradient background with app name and tagline
- **Search Bar:** Location and date selection
- **Map Section:** Interactive folium map with route visualization
- **Fare Details:** Breakdown of fare components
- **Vehicle List:** Available cars with details
- **Pricing Section:** Customizable fare calculation

## 📊 Sidebar Sections

- **About This App:** Application description
- **How It Works:** Step-by-step guide
- **Pricing Formula:** Detailed pricing breakdown
- **FAQ:** Frequently asked questions

## 🔗 API Endpoints (Optional Backend)

To extend with a backend API:
```python
import requests

# Get routes
response = requests.get('http://api.example.com/routes')

# Get available vehicles
response = requests.get('http://api.example.com/vehicles')

# Calculate fare
response = requests.post('http://api.example.com/fare', json={
    'pickup': 'Behala',
    'drop': 'Park Street',
    'distance': 150
})
```

## 🐛 Troubleshooting

### Port Already in Use
```bash
streamlit run carpool_streamlit_app.py --server.port 8502
```

### Model Loading Error
Ensure pickle files are in the same directory as the script.

### Map Not Displaying
Install streamlit-folium:
```bash
pip install streamlit-folium --upgrade
```

### Performance Issues
Cache data using @st.cache_resource decorator (already implemented).

## 📈 Performance Optimization

The app includes:
- Data caching with @st.cache_resource
- Lazy loading of models
- Efficient distance calculations
- Optimized map rendering

## 🔐 Security Considerations

- Validate user inputs
- Sanitize location data
- Rate limiting (implement in production)
- User authentication (if needed)
- HTTPS only (in production)

## 📝 Customization

### Change Colors
Edit the CSS in the `st.markdown` sections:
```python
'#667eea' - Primary purple
'#764ba2' - Secondary purple
```

### Add More Locations
Update `location_coordinates.pkl` with new locations.

### Modify Pricing Formula
Edit the `calculate_formula_fare()` function.

### Add More Features
- Real-time traffic integration
- User authentication
- Booking system
- Payment gateway
- Review/rating system

## 📞 Support

For issues or questions, refer to:
- Streamlit docs: https://docs.streamlit.io
- Folium docs: https://folium.readthedocs.io
- GitHub issues: [Your repo]

---

**Happy Carpooling! 🚗** 💚
