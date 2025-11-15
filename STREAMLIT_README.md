# 🚗 RideShare - Carpool Pricing Web Application

A modern, interactive Streamlit web application for calculating fair carpool fares with real-time route mapping and vehicle availability.

## 🌟 Features

### 1. **Beautiful Dashboard**
- Modern gradient UI inspired by professional ride-sharing apps
- Responsive design that works on desktop and mobile
- Clean layout with organized sections

### 2. **Interactive Route Mapping**
- Real-time Folium map integration
- Green marker for pickup location
- Red marker for destination
- **Blue connecting line showing the route**
- Distance calculation using Haversine formula

### 3. **Smart Fare Calculation**
- ML-based predictions using trained Random Forest model
- Formula-based transparent pricing
- Dynamic fare adjustments based on:
  - Distance (tiered pricing)
  - Fuel type (Diesel, Petrol, CNG, LPG)
  - Number of passengers (sharing discounts)
  - Peak hour surcharges

### 4. **Vehicle Display**
- Shows available cars for selected route
- Displays:
  - Car name and model
  - Number of seats
  - Fuel type
  - Vehicle age
  - Estimated fare per passenger

### 5. **Customizable Pricing**
- Real-time fare adjustment
- Fuel type selector
- Passenger count slider
- Peak hour toggle

## 📊 Dashboard Layout

```
┌─────────────────────────────────────────────────────────┐
│                    🚗 RideShare                         │
│    Share rides, save money, reduce carbon footprint    │
├─────────────────────────────────────────────────────────┤
│  [👥 10,000+ Users] [💰 Save 70%] [🌍 Eco-Friendly]   │
├─────────────────────────────────────────────────────────┤
│  From (City) │ To (City) │ Select Date │ [Search] ✕    │
├─────────────────────────────────────────────────────────┤
│  🗺️ ROUTE MAP                 │  💵 FARE DETAILS      │
│  [Interactive Map with        │  📏 Distance: XXX km  │
│   Blue Line Connecting        │  📅 Date: XXXX        │
│   Pickup to Destination]      │  ₹50 Base Fare        │
│                               │  ₹XXX Distance Charge │
│  Scale | Zoom Controls        │  ₹XXX Est. Fare       │
│                               │                        │
│  🚗 AVAILABLE VEHICLES        │                        │
│  ┌─────────────────────────┐  │                        │
│  │ Car Name                │  │                        │
│  │ 👥 Seats: 5             │  │                        │
│  │ ⛽ Fuel: Diesel          │  │                        │
│  │ 📅 Age: 3 years         │  │                        │
│  │ 💰 Fare: ₹XXX           │  │                        │
│  └─────────────────────────┘  │                        │
│  [More vehicles...]           │                        │
├─────────────────────────────────────────────────────────┤
│  📊 PRICING BREAKDOWN                                   │
│  Fuel Type: [Diesel ▼]  Passengers: [1 ─●─ 4]          │
│  ☐ Peak Hour Pricing                                   │
├─────────────────────────────────────────────────────────┤
│  ₹X.XX/km │ 2 Passengers │ ₹XXX Per Person │ ₹XXX Total│
│          TOTAL FARE FOR 2 PASSENGER(S)                │
│                    ₹XXX                                │
└─────────────────────────────────────────────────────────┘
```

## 🗺️ Map Features

After selecting pickup and drop locations:

1. **Dual Markers**
   - 🟢 Green marker: Pickup location
   - 🔴 Red marker: Destination location

2. **Route Visualization**
   - Blue polyline connecting both locations
   - Shows the direct route path
   - Hover for distance information

3. **Interactive Controls**
   - Zoom in/out
   - Pan/drag map
   - Full-screen option
   - Attribution controls

4. **Location Details**
   - Click markers for location names
   - Real-time distance display

## 💰 Pricing Formula

```
TOTAL FARE = (Base Fare + Distance Charge) × Multipliers

WHERE:
- Base Fare = ₹50
- Distance Charge = Distance × Rate (tiered)
- Multipliers = Fuel × Sharing × Peak × Route

TIERED DISTANCE RATES:
- 0-50 km: ₹3.50/km
- 51-150 km: ₹3.00/km
- 151-300 km: ₹2.50/km
- 301-500 km: ₹2.00/km
- 500+ km: ₹1.80/km

FUEL MULTIPLIERS:
- Diesel: 1.0× (baseline)
- Petrol: 0.95× (5% discount)
- CNG: 0.85× (15% discount)
- LPG: 0.90× (10% discount)

SHARING DISCOUNTS (per person):
- 1 passenger: 100% (no discount)
- 2 passengers: 55% each (45% discount)
- 3 passengers: 40% each (60% discount)
- 4+ passengers: 30% each (70% discount)

PEAK HOUR: +20% surcharge (7-10 AM, 5-8 PM)
```

## 🚀 Quick Start

### Installation

```bash
# 1. Clone or download the project
cd carpool-pricing

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the app
streamlit run carpool_streamlit_app.py
```

### Usage

1. **Select Locations**
   - Choose pickup location from dropdown
   - Choose drop location from dropdown
   - Select travel date

2. **Search Rides**
   - Click "Search Rides" button
   - Wait for map and fare calculation

3. **View Results**
   - See interactive map with blue route line
   - Review available vehicles
   - Check fare breakdown

4. **Customize Fare**
   - Select fuel type
   - Adjust number of passengers
   - Toggle peak hour pricing
   - See updated fare in real-time

5. **Book Ride**
   - Click on a vehicle
   - Confirm booking (in full app)
   - Proceed to payment

## 📍 Supported Locations

The app supports 12 Kolkata locations:

1. **Behala** - South Kolkata
2. **Tollygunge** - South Kolkata
3. **Ballygunge** - South Kolkata
4. **Park Street** - Central Kolkata
5. **Barasat** - North Kolkata
6. **Esplanade** - Central Kolkata
7. **Shyambazar** - North Kolkata
8. **Salt Lake** - East Kolkata
9. **Rajarhat** - East Kolkata
10. **Dumdum** - North Kolkata
11. **Howrah** - West Kolkata
12. **Garia** - South Kolkata

## 📊 Available Vehicles

The app shows real vehicles from the dataset with:
- Actual car models
- Real seat counts
- Actual fuel types
- Vehicle age information
- Calculated fares

## 🎨 Design Features

### Colors
- **Primary Purple:** #667eea
- **Secondary Purple:** #764ba2
- **Green (Success):** #2ca02c
- **Red (Alert):** #d62728

### Responsive Design
- Works on desktop (recommended)
- Tablet friendly
- Mobile responsive

### Accessibility
- Clear font sizes
- High contrast
- Proper spacing
- Descriptive labels

## 🔧 Technical Details

### Tech Stack
- **Frontend:** Streamlit + Folium
- **Backend:** Python (scikit-learn ML model)
- **Mapping:** Folium + Streamlit-Folium
- **Data:** Pandas, NumPy

### Performance
- Data caching with @st.cache_resource
- Lazy loading of models
- Optimized distance calculations
- Fast map rendering

### Architecture
```
carpool_streamlit_app.py
├── Load Data & Models
├── Helper Functions
│   ├── calculate_distance()
│   ├── predict_fare_ml()
│   ├── calculate_formula_fare()
│   └── get_available_cars()
├── UI Components
│   ├── Header Section
│   ├── Search Interface
│   ├── Results Section
│   └── Sidebar
└── Display Results
    ├── Map with Route
    ├── Fare Details
    ├── Vehicle List
    └── Pricing Breakdown
```

## 📱 Example Usage

### Example 1: Business Trip
```
From: Park Street (Central Kolkata)
To: Salt Lake (East Kolkata)
Distance: ~15 km
Fuel: Diesel
Passengers: 1
Peak Hour: Yes
Expected Fare: ₹320
```

### Example 2: Carpooling
```
From: Behala (South Kolkata)
To: Park Street (Central Kolkata)
Distance: ~20 km
Fuel: CNG
Passengers: 3
Peak Hour: No
Per Person Fare: ₹180 (60% discount!)
Total: ₹540
```

### Example 3: Long Distance
```
From: Dumdum (North Kolkata)
To: Rajarhat (East Kolkata)
Distance: ~30 km
Fuel: Petrol
Passengers: 2
Peak Hour: No
Per Person Fare: ₹225 (45% discount)
Total: ₹450
```

## 🌐 Deployment Options

### Option 1: Streamlit Cloud (Recommended)
- Free hosting
- Automatic updates
- Custom domain support
- Pro features available

### Option 2: Heroku
- Traditional deployment
- Custom configurations
- Paid dyno hours

### Option 3: AWS/Azure/GCP
- Full control
- Scalability
- Pay-as-you-go

## 📞 Sidebar Information

The sidebar includes:

### About This App
- Application description
- Key features
- Overview

### How It Works
- Step-by-step guide
- Usage instructions
- Navigation help

### Pricing Formula
- Detailed breakdown
- Rate tables
- Multiplier explanations
- Example calculations

### FAQ
- Common questions
- How fares are calculated
- Savings information
- Eco-friendly benefits

## 🔐 Security

- Input validation
- Safe data handling
- No personal data storage (in basic version)
- HTTPS recommended for deployment

## 📈 Future Enhancements

- [ ] User authentication
- [ ] Booking system
- [ ] Payment gateway
- [ ] Review/rating system
- [ ] Real-time traffic integration
- [ ] Historical pricing data
- [ ] Driver/passenger profiles
- [ ] Advanced search filters
- [ ] Multi-city support
- [ ] API integration

## 🐛 Known Issues

None currently reported. Please file an issue if you encounter any problems.

## 📝 License

This project is for educational purposes as a Final Year Project.

## 👨‍💻 Contributing

Feel free to customize and extend this app!

## 📞 Support

For questions or issues:
1. Check the FAQ section
2. Review documentation
3. Check GitHub issues
4. Contact developer

---

**Built with ❤️ using Streamlit | Made for your final year project 🎓**

**Happy carpooling! 🚗** 💚
