# Builder Component

This **Angular standalone component** seamlessly integrates with [Reveal](https://revealbi.io) to empower users to dynamically build dashboards or view single visualizations through an intuitive, point-and-click visualization catalog experience.

---

## 🚀 Overview

### Key Modes:

1. **Single Visualization Mode**
   - Click a visualization from the catalog to display it maximized in its own `RevealView` instance.

2. **Generated Dashboard Mode**
   - Select multiple visualizations to dynamically assemble a custom dashboard. Save or reset your dashboard effortlessly.

Driving adoption for BI and dashboards can be challenging. By providing an easy-to-use visualization catalog, organizations can accelerate data-driven decision-making. Users can create dashboards, save them for reuse, and integrate them into a shared or corporate catalog.

---

## 📽️ Video Walkthrough

Watch the step-by-step guide for this project on YouTube:

[![Watch the video](https://img.youtube.com/vi/G887Vy4UKfw/0.jpg)](https://youtu.be/G887Vy4UKfw)

---

## ✨ Features

### 🔍 **Visualization Catalog**
- **List of Visualizations:** Dynamically load a catalog of `VisualizationChartInfo` objects via the `RevealServerService`.
- **Icon-Based Interface:** Clean UI for selecting and adding visualizations.

### 📊 **Single Visualization Display**
- Maximize any visualization by clicking on it.
- Use a dedicated `RevealView` to provide an uninterrupted view of the chosen visualization.

### 🖼️ **Dashboard Creation**
- Combine selected visualizations into a dynamic dashboard.
- Generate an `RdashDocument` with multiple `VisualizationChartInfo` objects.

### 💾 **Save & Reset Dashboards**
- Handle naming collisions and dashboard overwrites using the `onSave` event.
- Include a custom “Clear/Reset” option to quickly start fresh.

---

## 🛠️ How It Works

### 1. **Retrieving Visualization Data**
The Reveal server fetches metadata for available visualizations, including titles, file references, and IDs. This populates the visualization list.

### 2. **Single Visualization Mode**
Clicking a visualization loads the associated `RevealView` and maximizes the view for detailed analysis.

### 3. **Dashboard Generation**
- Visualizations are added to a collection when selected.
- The `generateDashboard()` function creates a new `RdashDocument` from these visualizations, converting it to an `RVDashboard` for display.

### 4. **Saving Dashboards**
The `onSave` event ensures dashboard names are unique, prompting the user if overwrites are necessary.

### 5. **Resetting Dashboards**
The “Clear/Reset” option removes all visualizations, resetting the dashboard for new configurations.

---

## 🔑 Key Methods

### 1. **`loadVisualizationChartInfo()`**
- Retrieves visualization metadata and auto-selects the first visualization for single visualization mode.

### 2. **`listItemClick(item: VisualizationChartInfo)`**
- Loads a single visualization in a `RevealView`, showing it maximized.

### 3. **`iconClick(item: VisualizationChartInfo, event: MouseEvent)`**
- Adds a visualization to the dashboard if not already selected.
- Calls `generateDashboard()` to dynamically create the dashboard.

### 4. **`generateDashboard()`**
- Combines selected visualizations into an `RdashDocument`.
- Updates the `RevealView` with the newly generated dashboard.

### 5. **`setupRevealView()`**
- Configures the `RevealView` for dashboard management.
- Handles save events and custom menu options, including “Clear/Reset”.

### 6. **`resetDashboard()`**
- Clears all selected visualizations and resets the `RevealView`.

---

## 📚 Additional Details

### Visualization Catalog

Using the Reveal SDK DOM, visualizations from server-side dashboards are dynamically listed with titles, icons, and IDs. Users can:
- Click to view visualizations individually.
- Add them to a custom dashboard using the "+" icon.

### Dashboard Behavior

The dashboard creation logic is entirely client-side. Adding a new visualization recreates the dashboard view to accommodate the updated layout.

- **Auto Layout:** Ensures a clean and responsive design.
- **Client-Side Rendering:** Allows users to resize and rearrange visualizations.

---

## 🧰 Requirements

- Reveal Trial License
- [Reveal SDK Documentation](https://www.revealbi.io/)
- Angular environment for the client application.

---

## 🛠️ Getting Started

### Client Setup

1. Choose a client-side technology from one of the Client repo's
   - React
   - Angular
   - HTML
2. Clone the repository.
3. Open the Angular project folder.
4. Update the `endpoint` URL to point to your Reveal server.
5. Run the application.

### Server Setup

1. Choose a backend from one of the Server repo's:
   - .NET Core
   - Java
   - Node-js
   - Node-ts
2. Configure the Reveal Server to host your visualizations.
3. Start the server and ensure the endpoint matches the client configuration.

---

## 📚 Resources

- **Reveal Documentation:** [https://www.revealbi.io/](https://www.revealbi.io/)
- **GitHub Repository:** [https://github.com/RevealBi/sdk-samples-javascript](https://github.com/RevealBi/sdk-samples-javascript)
- **Additional Samples:** [https://github.com/RevealBi/sdk-samples](https://github.com/RevealBi/sdk-samples)

---

Bring your data to life with the **Builder Component**. Simplify dashboard creation, enhance user adoption, and accelerate data-driven insights with Reveal!

