# Builder Component

This Angular standalone component integrates with [Reveal](https://revealbi.io) to load and display visualizations, as well as dynamically build dashboards in a sinmple point-and-click visualization catalog experience.

## Overview

1. **Single Visualization Mode:**  
   When you click a visualization in the list, it’s displayed on its own (maximized) inside a `RevealView` instance.

2. **Generated Dashboard Mode:**  
   You can select multiple visualizations to dynamically assemble a combined dashboard and then save or reset that dashboard.

## Key Features

- **Load Visualization List**  
  Fetches a list of `VisualizationChartInfo` objects using `RevealServerService`.

- **Single Visualization Display**  
  On item click, loads the corresponding dashboard file, initializes a `RevealView`, and zooms into the chosen visualization.

- **Dashboard Generation**  
  Allows combining multiple visualizations into a single `RdashDocument`, converting them to an `RVDashboard`, and displaying the result in a separate `RevealView`.

- **Save & Reset Functionalities**  
  Uses the Reveal `onSave` event to manage naming collisions and existing dashboard overrides. Exposes a “Clear / Reset” menu item to clear the entire composite dashboard.

## Code Breakdown

Below is a high-level walkthrough of what `BuilderComponent` does, referencing key sections of the code:

1. **`loadVisualizationChartInfo()`**  
   - Retrieves visualization metadata from the server and automatically selects the first item to display in single-visualization mode.

2. **`listItemClick(item: VisualizationChartInfo)`**  
   - Handles single visualization loading.  
   - Creates a new `RevealView`, loads the associated dashboard file, and shows the chosen visualization in maximized mode.

3. **`iconClick(item: VisualizationChartInfo, event: MouseEvent)`**  
   - Stops event propagation to keep the UI consistent.  
   - Checks if the selected visualization is already in the dynamic dashboard list (`vizCollection`). If not, adds it, then calls `generateDashboard()`.

4. **`generateDashboard()`**  
   - Creates a new `RdashDocument` for the combined dashboard.  
   - Iterates through the selected visualizations (`vizCollection`), imports them from cached or newly loaded `RdashDocument`s, and generates a new `RVDashboard`.

5. **`setupRevealView()`**  
   - Initializes a `RevealView` for the dashboard container.  
   - Handles saving logic (`onSave` event), which prompts for a valid name and checks for existing dashboards on the server.  
   - Configures `onMenuOpening` to hide “Export” and add a custom “Clear / Reset” menu item.

6. **`resetDashboard()`**  
   - Clears all selected visualizations, resets the combined dashboard, and sets up the environment for a fresh start.

## How It Works

1. **Retrieving Data**  
   `RevealServerService` is used to fetch a list of available charts (each with an ID, name, file reference, etc.).

2. **Single Visualization Display**  
   A dedicated reveal view is used whenever you select one visualization, so you can quickly preview it without affecting the combined dashboard.

3. **Dashboard Building**  
   You can click the icon to add a visualization to your custom dashboard. The code imports each visualization from its original source `RdashDocument` into a brand-new `RdashDocument`.

4. **Saving & Validation**  
   The component checks for duplicate names on save. If a duplicate is found, it prompts the user to confirm overwriting the existing dashboard. This logic lives in `onSave`.

5. **Resetting**  
   The “Clear / Reset” menu item helps you wipe the combined dashboard clean, leaving you free to start building a new one.

## Getting Started
Each repository has a readme for getting started on both the client and the server.

## Requirements

- Reveal Trial License
