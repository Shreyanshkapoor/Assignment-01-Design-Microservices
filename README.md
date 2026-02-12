## How I Built This (WeatherApp)

### 1. Project Setup
- Created the project folder and initialized a Git repository.
- Built the basic project structure using:
  - `index.html`
  - `style.css`
  - `script.js`
- Linked all files and verified the initial layout in the browser.

### 2. UI Development
- Designed a clean and responsive interface containing:
  - Search input field
  - Search button
  - Weather result display section
- Used **CSS Flexbox** to align elements properly and ensure responsiveness.

### 3. API Integration
- Integrated the **OpenWeather API** to fetch live weather data.
- Used JavaScript `fetch()` to send API requests.
- Converted the response into JSON format and extracted:
  - City name
  - Temperature
  - Weather condition
  - Humidity
  - Wind speed

### 4. User Interaction Logic
- Added event listeners for the search button and input field.
- Triggered the API request when the user enters a city name.
- Dynamically updated the DOM to display results without page reload.

### 5. Error Handling
- Implemented validation for:
  - Empty input
  - Invalid city names
  - Network/API errors
- Displayed user-friendly error messages when needed.

### 6. Testing & Deployment
- Tested the application with multiple city names to verify accuracy.
- Deployed the project using **GitHub Pages** for public access.
