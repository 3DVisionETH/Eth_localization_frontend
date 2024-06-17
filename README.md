# Architecture Overview of Localizr Project


Localizr project is divided into three main layers: Services (API Backends), Session (Stateful), and Views (SwiftUI). 

# DEMO

https:/github.com/3DVisionETH/Eth_localization_frontend/blob/main/Localizr_demo-2

## Modes of Operation

Localizr operates in two modes: **Frontend Only** and **Backend Integrated**. A service factory pattern is used to switch between these modes based on the environment configuration.


## Layers and Components
![Immagine 14-06-24 - 19 34]([https:/3DVisionETH/Eth_localization_frontend/assets/109732478/993382f4-1c71-4ac7-8d48-8c292a1d1c53)



### Services (API Backends)

- **BuildingService**
  - Responsible for fetching floor plans and room information.

### Session (Stateful)

- **LocalizerSession**
  - Manages 6-DOF (Degrees of Freedom) pose and image uploads.
  - Interacts with both the BuildingService and NavigationSession.

- **NavigationSession**
  - Manages route information.
  - Relies on data from BuildingService and LocalizerSession to provide navigation routes.

### Views (SwiftUI)

- **AppDelegate & AppTheme**
  - Handles application lifecycle and theme settings.

- **ContentView**
  - The main user interface container.

- **MapARToggle, NavigationSearch, MapOverlay, LocalizeOverlay**
  - Specific views for toggling AR mode, searching specific rooms, and displaying map overlays.


## Execution Flow

**Initialization:**

AppDelegate and AppTheme set up the application and theme.

**Data Fetching:**

BuildingService fetches required data (floor plans, room info) from the local database (frontend only) or backend APIs (backend mode).

**Session Management:**

LocalizerSession localize you in the building.
NavigationSession calculates routes based on the provided localization and building data.

**UI Rendering:**

UI components interact with sessions to provide real-time updates and user interactions, displaying maps, location and path to final destination




