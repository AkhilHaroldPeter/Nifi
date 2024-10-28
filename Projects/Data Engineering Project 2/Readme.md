# NiFi Flow Loading Instructions

![Project Screenshot](https://github.com/AkhilHaroldPeter/Nifi/blob/master/Projects/Data%20Engineering%20Project%202/NifiFlow.png)

This document provides step-by-step instructions on how to load and run a NiFi flow template. Please ensure you have the necessary dependencies installed before proceeding.

## Flow Overview

This NiFi flow automates the entire data ingestion, processing, and reporting pipeline for credit card transaction analysis, using Python scripts and dynamic attribute management for customizable output formats.
1. **GenerateFlowFile (Scheduler)**
This processor is used to trigger the entire NiFi flow. The GenerateFlowFile processor is scheduled to run every 2 hours but can be adjusted based on specific project requirements. This flexible scheduling initiates the pipeline automatically at set intervals.

2.**ExecuteStreamCommand: Download Kaggle Data**
This processor calls a Python script ```(Kaggle_data_download.py)``` to hit the Kaggle API and download the required credit card transaction dataset. The script uses the provided API key to authenticate and pull data from the Kaggle repository, saving it to a specified location

3. **ExecuteStreamCommand: Create Table & Load Data**
After downloading, this processor runs the script ```(Table_Creation_and_data_loading.py)``` to create a new table if it doesn't already exist in the target database. The script checks for table existence and then loads the downloaded data, ensuring uniqueness and maintaining data integrity.

4. **UpdateAttribute: Set Attributes for Next Steps**
This processor updates specific attributes or variables dynamically. The attributes define parameters like file formats (CSV, Excel, JSON, etc.) or SQL script selection, which will be used by downstream processors. This flexibility allows for dynamic control over the pipeline's processing and output generation.

5.**Process Group: Execute Analysis & Output Generation**
The flow then moves into a process group containing the following steps:
- **ExecuteStreamCommand 1**: This processor runs the script ```(sql_analysis.py)``` based on the attributes set earlier. The script executes SQL queries to perform comprehensive analysis on the ingested transaction data. The queries may focus on various insights like spending patterns, fraud detection, or customer segmentation.
- **ExecuteStreamCommand 2**: This processor runs a final script ```(Output_Generation.py)``` to generate reports in the specified output formats. Based on the attributes (```csv: true```, ```excel: false```, etc.), the script exports the analysis results in one or more formats such as CSV, Excel, JSON, Parquet, Document, or PDF, making it adaptable to different reporting needs.

**End-to-End Automation & Flexibility**: This NiFi flow showcases end-to-end automation from data ingestion to analysis and output generation. Its attribute-based architecture provides flexibility in data handling, allowing users to switch between different scripts and output formats without modifying the core flow.


## Prerequisites

Before loading the NiFi flow template, ensure you have the following installed on your machine:

1. **Java Development Kit (JDK)**: Apache NiFi requires Java 8 or later. You can download the latest JDK from the [Oracle JDK download page](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or use [OpenJDK](https://openjdk.java.net/install/).

2. **Apache NiFi**: Download the latest version of Apache NiFi from the [official Apache NiFi downloads page](https://nifi.apache.org/download.html).

### Installation Instructions

#### 1. Install Java

- For Windows, Mac, or Linux, refer to the following YouTube videos:
  - [How to Install Java on Windows](https://www.youtube.com/watch?v=Ghpq2mBtDs0)
  - [How to Install Java on Mac](https://www.youtube.com/watch?v=PQk9O03cukQ)
  - [How to Install Java on Ubuntu](https://www.youtube.com/watch?v=vVrIDJ--GOA)

#### 2. Install Apache NiFi

- Download Apache NiFi from the official page.
- Unzip the downloaded file to your preferred directory.

- For detailed installation instructions, check the following YouTube videos:
  - [Installing Apache NiFi on Windows](https://www.youtube.com/watch?v=dYhI6o-TO4c)
  - [Installing Apache NiFi on Ubuntu](https://www.youtube.com/watch?v=lsS-vb1G1t8)

## Loading a NiFi Flow Template

Once you have installed NiFi, follow these steps to load the NiFi flow template:

1. **Start Apache NiFi**:
   - Navigate to the `bin` directory of your NiFi installation.
   - Open a terminal or command prompt and run the following command:
     ```bash
     ./nifi.sh start  # For Linux/Mac
     nifi.bat start   # For Windows
     ```

2. **Access the NiFi UI**:
   - Open your web browser and go to [http://localhost:8080/nifi](http://localhost:8080/nifi) or [http://localhost:8443/nifi/](http://localhost:8443/nifi/).

3. **Import the Template**:
   - Click on the **Template** icon (a small pencil and paper icon) on the top menu bar.
   - Select **Upload Template** from the dropdown menu.
   - In the file dialog, choose the NiFi flow template file (usually with a `.xml` extension) you want to import.

4. **Add the Template to the Canvas**:
   - After the template is uploaded, find it in the list of available templates.
   - Drag and drop the template onto the NiFi canvas to add it.

5. **Configure the Processors**:
   - Double-click on each processor to configure it with the necessary settings (e.g., input sources, database connections).

6. **Start the Processors**:
   - Select the processors you want to start by clicking on them.
   - Click on the **Start** button (the play icon) in the toolbar to start the selected processors.

## Troubleshooting

- If you encounter issues starting NiFi, check the logs located in the `logs` directory of your NiFi installation for any error messages.

## Additional Resources

- For more detailed information on Apache NiFi, refer to the official [Apache NiFi Documentation](https://nifi.apache.org/docs.html).
- You can find a variety of tutorials and resources on YouTube, such as:
  - [Apache NiFi Tutorials](https://www.youtube.com/results?search_query=apache+nifi+tutorial)

Feel free to reach out if you have any questions or need further assistance!

