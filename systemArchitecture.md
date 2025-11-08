#  System Architecture – H-eye

##  Overview
H-eye is a mobile app hotel management system built with a **React frontend**, **Node.js backend**, and **MongoDB database**.  ###
The goal is to provide a reliable and scalable platform for hotel owners to track daily operations.


##  Architecture Layers
### 1. Microcontroler
- Arduino

### 1. Frontend-mobile app (Client)
- **Technology**: React Native + Tailwind CSS  
- **Role**: Displays all UI components — dashboard, reports  
- **Communication**: Sends requests to backend via REST APIs  
- **Hosting**: Vercel  

### 2. Backend (Server)
- **Technology**: Node.js + Express  
- **Role**: Handles all logic — authentication, data validation, and communication with the database  
- **API Routes**:
  - `/api/signup`
  - `/api/signin`
  - `/api/register-hotel`
  - `/api/room-data/active` 
  - `/api/room-data/inactive`
  - `/api/tracking-power/active rooms`
  - `/api/analytics/total-rooms-used`

### 3. Database
- **Technology**: MongoDB  
- **Role**: Stores hotel activity information  
- **Hosting**: MongoDB Atlas (cloud-based)-

---
## Data Flow and Authentication Process

### Authentication Flow
The authentication flow manages secure access for users using either email and password or Google Signin.

#### - Username and Password
- The user opens the app and enters credentials.  
- The app uses  `/api/signin`.  

#### - Google Sign-In
- The user taps Sign in with Google. 
- The app use `/api/signin`. 

### Room Activity and Power Tracking Flow
 - The Hotel server using the arduino monitors room occupancy and power usage.  
 - It uses the api  `/api/tracking-power/active-rooms`  

## Total
- This shows analytic data for the user in form of a graph like (power consumed in a time range)
- It uses the api `/api/analytics/total-rooms-used`

##  How Components Communicate

```text
User (browser)
   ↓
Frontend (React)
   ↓ REST API calls
Backend (Node.js / Express)
   ↓
Database (MongoDB)

