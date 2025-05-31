# CrossWise - Smart Border Crossing Management System

## Overview

CrossWise is an intelligent border crossing management system designed to help travelers efficiently cross the US-Mexico border at San Ysidro and Otay Mesa. The system provides real-time wait times, predictive analytics, live camera feeds, weather information, and comprehensive tools for planning border crossings.

## Features

### Core Features

1. **Real-Time Border Wait Times**
   - Live updates for both San Ysidro and Otay Mesa crossings
   - Separate times for Standard Vehicles, SENTRI lanes, and Pedestrian crossings
   - Color-coded indicators (green ≤30min, yellow 31-89min, red ≥90min)

2. **Live Border Camera Feed** (`/livefeed`)
   - Real-time video streaming from border crossings
   - Timelapse generation for past 5 hours
   - Historical video playback with calendar navigation
   - Automated video archival system

3. **Predictive Analytics**
   - Machine learning models for wait time predictions
   - Historical pattern analysis
   - Peak time identification

4. **Weather Integration** (`/weather`)
   - Current weather conditions
   - Weekly forecast with temperature trends
   - Visual charts using Chart.js

5. **User Management System**
   - User authentication (username/password and facial recognition) (`/login`)
   - Profile management with customizable settings
   - Friend system with notifications
   - User statistics tracking

6. **Community Features**
   - Border crossing feedback system (`/crosswiseforms`)
   - Traffic incident reporting (`/traffic-report`)
   - Event calendar for San Diego area activities (`/calendar`)

7. **Planning Tools**
   - Interactive directions with Google Maps integration (`/directions`)
   - Route optimization based on current wait times
   - Alternative crossing suggestions

## Architecture

### Frontend
- **Framework**: Jekyll static site generator
- **Styling**: Tailwind CSS with custom dark theme
- **Charts**: Chart.js for data visualization
- **Maps**: Google Maps API for directions

### Deployment
- **Frontend**: GitHub Pages
- **Backend**: AWS EC2 instance
- **CI/CD**: GitHub Actions for automated deployment

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/illuminati1618/CrossWise.git
   cd CrossWise
   ```

2. **Setup**
   ```bash
   source venv/scripts/activate
   ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Run the development server**
   ```bash
   make
   ```
   The site will be available at `http://localhost:4887/CrossWise/`

## Project Structure

```
CrossWise/
├── _layouts/          # Jekyll layout templates
│   ├── tailwind.html  # Main layout with Tailwind CSS
│   ├── post.html      # Blog post layout
│   └── base.html      # Base HTML structure
├── _includes/         # Reusable components
│   ├── nav/           # Navigation components
│   └── theme/         # Theme-specific includes
├── _posts/            # Blog posts and generated content
├── _notebooks/        # Jupyter notebooks (converted to posts)
├── navigation/        # Main site pages
│   ├── index.html     # Homepage
│   ├── livefeed.html  # Live camera feed
│   ├── weather.md     # Weather dashboard
│   ├── calendar.html  # Event calendar
│   ├── contact.md     # Contact us page
│   ├── directions.html # Google Maps directions
│   ├── help.md         # Help page for users
│   ├── historicaldata.md  # Graphical historical data
│   ├── search.html        # User search feature
│   └── authentication/    # Login/profile pages
├── assets/
│   ├── js/
│   │   └── api/       # API configuration and utilities (config.js, login.js)
│   ├── css/           # Stylesheets
│   └── images/        # Static images
├── scripts/           # Setup and utility scripts
└── _config.yml        # Jekyll configuration
```

## Key Components

### 1. Live Feed System (`navigation/livefeed.html`)
- Fetches video clips from bordertraffic.com
- Implements a rolling window to find available videos
- Supports timelapse generation via backend API
- Features playback controls and historical browsing

### 2. Authentication System
- **Login Methods**: 
  - Traditional username/password
  - Facial recognition using backend API
- **Session Management**: Cookie-based with JWT tokens
- **Profile Features**: Avatar upload, bio, friend system

### 3. Weather Integration (`navigation/weather.md`)
- Fetches data from National Weather Service API via backend proxy
- Displays current conditions and 7-day forecast
- Interactive chart.js visualizations

### 4. Border Wait Times
- Real-time data from CBP (Customs and Border Protection)
- Automatic refresh every 5 minutes
- Color-coded wait time indicators

### 5. Feedback Systems
- **Border Crossing Feedback** (`/crosswiseforms`): Users report actual wait times
- **Traffic Reports** (`/traffic-report`): Incident reporting system
- Data stored in backend for ML model improvement

## API Integration

### Backend API Endpoints (Python Flask)

READ BACKEND README FOR DETAILS!
https://github.com/illuminati1618/CrossWise_Backend2025/

### External APIs
- **Google Maps API**: Directions and mapping
- **CBP API**: Border wait times (proxied through backend)
- **National Weather Service API**: Weather data
- **BorderTraffic.com**: Video feeds

## Development

### Running Tests
```bash
# Convert Jupyter notebooks
make convert

# Clean generated files
make clean

# Stop the server
make stop
```

### Adding New Features

1. **Create a new page**: Add to `navigation/` directory
2. **Add to navigation**: Update `_layouts/tailwind.html`
3. **Create API endpoint**: Modify backend Flask application
4. **Update configuration**: Edit `_config.yml` if needed

## Deployment

### GitHub Pages (Frontend)
1. Enable GitHub Pages in repository settings
2. Set deployment source to GitHub Actions
3. Push to main branch triggers automatic deployment

---

**Note**: This project requires API keys for full functionality.
