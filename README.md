# Architecture Overview of Localizr Project


Localizr project is divided into three main layers: Services (API Backends), Session (Stateful), and Views (SwiftUI). 


## Modes of Operation

Localizr operates in two modes: **Frontend Only** and **Backend Integrated**. A service factory pattern is used to switch between these modes based on the environment configuration.



## Layers and Components

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





