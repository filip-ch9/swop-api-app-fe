# SWOP API Frontend

This is the frontend application for the SWOP API. It allows users to interact with the API by providing input values for source currency, target currency, and amount, and fetching exchange rate information from the backend.

## Usage

1. Clone this repository to your local machine.
2. Install dependencies using npm or yarn:

   ```bash  
   npm install# or  
   yarn install
   ```  
3. Start the development server:
   ```bash  
   npm run serve  
   # or  
   yarn serve  
   ```  
4. Open your browser and navigate to http://localhost:8082 to access the application.
5. Enter the source currency, target currency, and amount in the respective input fields.
6. Click the "Get Exchange Rate" button to fetch the exchange rate information from the backend.
7. The exchange rate information will be displayed below the button.

## Dependencies
Vue.js  
Axios

## Backend API
This frontend application interacts with the SWOP API [backend](https://github.com/filip-ch9/swop-api-app) to fetch exchange rate information. Ensure that the backend server is running and accessible from this frontend application.