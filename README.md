# A Guide to setup and use [`Plantuml`](https://plantuml.com )


## Requirements:
 - JRE: https://adoptopenjdk.net/
 - GraphViz: https://graphviz.org/download/
 - VSCode IDE: https://code.visualstudio.com/Download
 - vs code Plugin: https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml


## Setup:
 - Install everything listed above
 - If not already done, add `JAVA_HOME` to system/env variables with path to `\bin\java.exe` , this step is mendatory
 - [Optional] Add Plant UML jar path in system/env variables to access it easily anywhere
    - You can also add path to `bin\dot.exe` from Graphviz to env variable as `GRAPHVIZ_DOT`, makes it easy to export the diagrams into PDF
 - Open `Preference Settings(JSON)` in vscode and add following:
    - `"commandArgs": "-DPLANTUML_LIMIT_SIZE=8192", `
     - allows bigger diagram generation
    - `"jarArgs": "-config PATH_TO_CONFIG_FILE",`
     - allows custom color and diagram configuration for all digram when exporting
    - `"plantuml.jar": "PATH_TO_JAR_FILE",`
     - provides path to your latest extracted/downloaded jar file
 - [Optional] Associate following extensions to open in VS Code:
   - .plantuml
   - .puml
   - .pu
   - .txt


## Create diagram files:
 - Create a simple file with any of the extensions above
 - add your required code for diagram in the file 
   - you can refer to this site to check how PlantUML works: https://www.planttext.com
 - Save the file as required.

## Generate Diagrams: 
You can create diagram in two ways:
 - Using vs code extension (allows quick diagram generation, no customized output)
 - Using command line (allows complete customization of output diagram, slow and complex to use for beginners)

## Using vs code:
 - Open the diagram file in vs code
 - [Optional] check diagram preview by pressing `Alt+D`
 - Press `ctrl+shift+P`  for a list commands 
 - Search `>PlantUML: Export Current Diagram` & select the same option
 - Select preferred output format

The output files will be created in the out  folder in the same directory as the diagram source file(`*.puml`)

## Using command line:
 - Open Command/terminal in smae directory as the source file
 - Use following command to generate a pdf from the diagram:
   
   `java -jar %plant_uml% diagram.puml -o output -progress -tpdf`
   - `%plant_uml%` is the enviroment variable name, you can replace this with path to `plantuml.jar` file
   - `diagram.puml` is the source file
   - `-o output`  creates output folder in the same directory and created the pdf inside it
   - `-tpdf` creates a PDF of the diagram there are many other format options for exporting a diagram
   - `-progress`  shows diagram creation progress in the cmd/terminal
   - [Optional] For bigger/huge diagrams add this to command: `-DPLANTUML_LIMIT_SIZE=8192`
   - For customizing the output of the diagram provide the configuration file path: `-config PATH_TO_CONFIG_FILE`

The final command should look like this:

`java -jar C:\\TOOLS\\PlantUML\\plantuml.jar diagram.puml -o output -progress -config C:\\TOOLS\\PlantUML\\config\\plantuml.config -DPLANTUML_LIMIT_SIZE=8192  -tpdf`


## Notes:
My setup is in a Windows environment with my specific requirements, so some specific steps might not work with your system. Please adjust the settings according to your own sytem and requirements.
