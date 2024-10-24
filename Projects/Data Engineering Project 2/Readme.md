# NiFi Flow Loading Instructions

![Project Screenshot]([images/screenshot.png](https://github.com/AkhilHaroldPeter/Nifi/blob/master/Projects/Data%20Engineering%20Project%202/NifiFlow.png))

This document provides step-by-step instructions on how to load and run a NiFi flow template. Please ensure you have the necessary dependencies installed before proceeding.

## Prerequisites

Before loading the NiFi flow template, ensure you have the following installed on your machine:

1. **Java Development Kit (JDK)**: Apache NiFi requires Java 8 or later. You can download the latest JDK from the [Oracle JDK download page](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or use [OpenJDK](https://openjdk.java.net/install/).

2. **Apache NiFi**: Download the latest version of Apache NiFi from the [official Apache NiFi downloads page](https://nifi.apache.org/download.html).

### Installation Instructions

#### 1. Install Java

- For Windows, Mac, or Linux, refer to the following YouTube videos:
  - [How to Install Java on Windows](https://www.youtube.com/watch?v=p1c6XwslrJo)
  - [How to Install Java on Mac](https://www.youtube.com/watch?v=kl0j2YXNsOc)
  - [How to Install Java on Ubuntu](https://www.youtube.com/watch?v=0KeUq8kV3Sg)

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

