## Field Collection & Project Management System (OutSystems)

### Overview
This project is a comprehensive field data collection and project management system built with OutSystems 11. It's designed to streamline the process of collecting georeferenced data in the field and providing project managers with powerful tools to visualize and manage this data.

The system comprises two distinct applications: a Mobile PWA for field workers to mark collection points using their device's GPS, and a Reactive Web Application for project managers to oversee all collected data on an interactive map.

### Key Features

#### For Field Workers (Mobile PWA)
* **GPS-Powered Point Collection:** Workers can accurately mark their current location (latitude, longitude, altitude, accuracy) as a collection point.
* **Detailed Data Input:** For each point, workers can input a custom name, select a collection type (e.g., "Soil Sample," "Infrastructure Check," "Environmental Observation"), add descriptions, and optionally attach photos.
* **Personalized Point List:** View a list of all points they have personally marked, with quick access to details.
* **Individual Point Details with Map:** Click on any marked point to see its full details, including its location displayed on an interactive Google Map.

#### For Project Managers (Reactive Web Application)
* **Centralized Map View:** An interactive Google Map displays all collection points from all workers, providing a comprehensive overview of field operations.
* **Point Management:**
    * **Editing:** Managers can modify details of any collection point, including its name, type, description, and status.
    * **Status Updates:** Change the status of a point (e.g., "Pending," "Verified," "Problem") to track progress and flag issues.
    * **Deletion:** Remove invalid or unwanted collection points from the system.
* **Data Table View:** A detailed table listing all collection points, allowing for quick review and access to management actions.
* **Project and User Management (Planned/Expandable):** The underlying data model supports project and user assignments, making it ready for future expansion into more granular project and team management.

### Technical Stack & OutSystems Features
This project showcases proficiency in OutSystems 11 development, leveraging a variety of its capabilities:

* **OutSystems 11 (Service Studio):** Developed entirely within the OutSystems 11 platform.
* **Reactive Web Applications:** For the Project Manager's dashboard, providing a modern and responsive web experience.
* **Mobile PWAs (Progressive Web Apps):** For the Field Worker's application, offering an app-like experience without app store installation.
* **REST API Integration:** Utilizes Google Maps Platform APIs for interactive map displays and geocoding functionalities.
* **Device Geolocation API:** Integrates with native device GPS capabilities (via OutSystems Forge Component: Location Plugin) for precise location capturing.
* **Database Design:** Robust entity model (`Project`, `CollectionPoint`, `CollectionPointType`) with relationships and static entities for data integrity.
* **Client & Server-Side Logic:** Demonstrates effective use of OutSystems Client Actions for UI interactions and device integration, and Server Actions for data persistence.
* **User & Role Management:** Leverages OutSystems built-in security features for different user profiles (Field Worker, Project Manager).
* **OutSystems Forge Components:** Utilizes pre-built components from the OutSystems Forge (e.g., Google Maps Reactive, Google Maps Mobile, Location Plugin) to accelerate development and enhance functionality.
* **UI/UX Patterns:** Implementation of common UI patterns for lists, forms, modals, and interactive maps.
* **Secure API Key Handling:** Demonstrates best practices for storing and retrieving sensitive API keys using OutSystems Site Properties, restricted via Google Cloud Console.

### Architecture
The system is architected into two separate OutSystems Applications to manage distinct user experiences and deployment types:

* **`ProjectManagementApp` (Reactive Web):** Hosts the `ProjectManagement_RW` module, containing core data entities and the manager's dashboard.
* **`FieldWorkerApp` (Mobile PWA):** Hosts the `FieldWorker_MA` module, responsible for the field worker's data collection interface.

Data entities are centrally managed and exposed from `ProjectManagement_RW` to `FieldWorker_MA`, ensuring a single source of truth for all collection points.

### How to Run This Project
1.  **OutSystems Environment:** You will need an OutSystems 11 personal environment or cloud environment.
2.  **Service Studio:** Open the `.oml` files (or solutions) for `ProjectManagementApp` and `FieldWorkerApp` in OutSystems Service Studio 11.
3.  **Google Maps API Key:**
    * Obtain a Google Maps API Key from the [Google Cloud Console](https://console.cloud.google.com/).
    * Enable the `Maps JavaScript API`, `Geocoding API`, and potentially `Places API`.
    * **Restrict your API key** by `HTTP referrers` (for your OutSystems environment domains, e.g., `*.outsystemscloud.com/*`, and `localhost:port/*`) and `API restrictions` (to only the necessary Google Maps APIs).
4.  **Forge Components:** Ensure the following Forge components are installed in your environment and referenced in the respective modules:
    * `Location Plugin` (for `FieldWorker_MA`)
    * `Google Maps Mobile` (or similar, for `FieldWorker_MA`)
    * `Google Maps Reactive` (or similar, for `ProjectManagement_RW`)
5.  **Site Properties:** In your OutSystems Service Center, navigate to each module (`ProjectManagement_RW` and `FieldWorker_MA`) and set the value for the `GoogleMapsAPIKey` Site Property with your Google Maps API Key.
6.  **Publish:** Publish both applications from Service Studio.
7.  **Access:**
    * **Field Worker App:** Access via your mobile browser (PWA) or by building a native app.
    * **Project Manager App:** Access via your web browser.

### Future Enhancements
* User authentication and authorization based on roles (Manager, Worker).
* Filtering and search capabilities for collection points on the manager's dashboard.
* Ability to upload multiple photos per point.
* Offline capabilities for the mobile app (saving data locally and syncing when online).
* Reporting and analytics features for project managers.
* Integration with other Google Maps APIs like Places Autocomplete.
