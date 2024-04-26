# Frontend - Javascript




## 1. Getting started

This section of the development guide provides an overview of how to get started with the Frontend-JS project, setting up the development environment, and running the application locally.

###  Prerequisites
Before you start, ensure you have the following installed on your system:

**Node.js**: A JavaScript runtime built on Chrome's V8 JavaScript engine. The project requires Node.js version 12.x or higher. You can download it from Node.js official website.
**npm**: Node Package Manager, comes with Node.js, used for managing dependencies.
**Git**: Version control system to clone the repository. Download from Git's official site.


###  Clone the repo
First, clone the Frontend-JS repository from GitHub:
 ```
 git clone https://github.com/planimation/Frontend-JS.git
 cd Frontend-JS
 ```


###  Installing Dependencies
After cloning the repository, install the project's dependencies. Run the following command in the project directory:
```
npm install
```


###  Running the Application locally
To start the development server and run the application locally, use:
```
npm start
```
This command will start a development server and open the application in your default web browser. The development server typically runs on http://localhost:3000.


## 2. Architecture Overview


###  Data flow
The data flow within the Frontend-JS application can be particularly observed in the scenario where a user uploads domain, problem, and animation plan (AP) files:

1. File Upload at /problem:
Users navigate to the /problem page, where they use the provided drop zones to upload three PDDL files: domain, problem, and animation file.
Each file is handled by the DropZone component, which validates and reads the file content as soon as it's dropped into the respective zones.  
<br>
2. FormData Preparation and API Interaction:
Once all necessary files are uploaded and validated, the DropAndFetch component collects these files and packages them into a FormData object.
This FormData object is then sent to the backend via a POST request to a specific API endpoint (e.g., https://planimation.planning.domains/upload/pddl). This endpoint is responsible for processing the PDDL files and returning a visualization format, typically a VFG JSON object.  
<br>
3. Response Handling and Storage:
Upon receiving the response from the backend, the application store the returned VFG JSON in browser's local storage and redirect to page Fore. This JSON contains the necessary data to render the planning visualization.  
<br>
4. Visualization Rendering:
With the VFG JSON object at hand, the application transitions to a visualization page where the planning results are visualized.


### Directory Structure
```
Frontend-JS/
│
├── src/                      # Source files for the application
│   ├── components/           # Reusable components
│   │   ├── alertInFormat.jsx # Alert component for error messages
│   │   └── navigationBar/    # Navigation bar component
│   ├── pages/                # Components representing entire pages
│   │   ├── HomePage/         # 
│   │   ├── PageOne/          # Initial page for file upload
│   │   │   ├── dropAndFetch.jsx  # Manages file upload and backend communication
│   │   │   └── dropZone.jsx      # Drop zone component for file input
│   │   ├── PageTwo/          # Options to upload VFG directly
│   │   ├── PageThree/        # User Manual
│   │   ├── PageFour/         # Process VFG and display visualizaton
│   │   └── PageFive/         # Handle messages received from the plugin
│   ├── plugin/
│   └── Styles/
│
├── public/                   # Static assets
│   └── index.html            # HTML template
│
├── scripts/                  # 
│
├── config/                   # Project configuration files
│   └── webpack.config.js     # Webpack configuration
│
├── cypress/                  # 
│
└── package.json              # Project metadata and dependencies
```



## 3.  Components


