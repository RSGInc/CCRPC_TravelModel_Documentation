# Introduction
#### Last updated: 5/20/2026

The Chittenden County Regional Planning Commission Travel Demand Model,
Version 4.0.0 (“the model”) is an integrated transportation demand model
developed by Resource Systems Group (RSG) for the Chittenden County
Regional Planning Commission.

The model estimates the movement of people and vehicles within the
region during an average fall weekday in 2015. The 2015 Model is a daily
model with hourly traffic assignments and is implemented in TransCAD
7.0. The model includes 528 internal Transportation Analysis Zones
(TAZs) covering the 19 municipalities in Chittenden County. Traffic
entering and exiting the region does so through 17 external zones.

Transportation planners can use the model to perform comprehensive
regional transportation analyses, and to evaluate traffic impacts
resulting from:

- multi-modal transportation improvements,

- changes in traveler behavior,

- changes to the roadway system,

- changes in land use activity, and

- implementation of demand management strategies.

Details regarding the model structure, data sources, and calibration are
presented in the CCRPC Regional Travel Model Documentation report from
September 5, 2017.

The purpose of this User Guide is to describe the steps necessary to:

- Install the model,

- Create new scenarios for model analyses, and

- Run the model to generate results for analysis

# Installing the Model

This section outlines the procedure to follow to successfully install,
set-up, and begin using the CCRPC Regional Travel Model. The following
sections outline the software and hardware requirements, installing the
model, installing the TransCAD add-in and finally using the model.

## Modeling Requirements

The minimum software requirements to run the model include:

- TransCAD Version 7.0

- Build 12365

- The minimum hardware system requirements to properly execute a model run
include:

- 1 GB RAM - Minimum

- 30 GB – Minimum of free hard disk space

## Model Directory Structure

The model directory structure is outlined below:

- **Drive:\CCRPC\** - Model root directory

- **Scenario Name(s)\\** - User defined scenario name(s) (e.g. “2015_Base”, “2020”, “2030”, “2035”, “2050wTIP”; Create as many of these directories as there are scenarios.

- **Inputs\** - Model Input Files 

  - **1_Highway Network** - Highway Network Inputs

  - **2_Transit Network** - Transit Network Inputs

  - **3_TAZ and TripGen** - TAZ and land-use data

  - **4_Trip Distribution** - Distribution Inputs

  - **5_Mode Choice** - Travel Mode Inputs

  - **6_Diurnal Distribution** - Diurnal Distribution Inputs

  - **7_Assignment** - Assignment Inputs

  - **8_Reports** - Model Reports

- **Outputs\\** - Model output files

  - **1\_ Network** - Network outputs

  - **2_Transit** - Transit outputs

  - **3\_ TripGen** - Trip generation outputs

  - **4_TripDist** - Trip distribution outputs

  - **5_ModeChoice** - Mode choice outputs

  - **6_Diurnal** - Diurnal Distribution outputs

  - **7_Assign** - Assignment outputs

  - **8_Reports** - Model reports

- **Resource Files\\** - Resource files for model installation including the model user interface

## Installing the Model

Copy the model scripts and configure the interface control files:

1.  Paste the GISDK macros folder (“**Resource Files**”) and built-in **scenarios** folders (“2015_Base”,…,), along with the **CCRPC_mod.bin** and .DCB files to the root directory location chosen by the user.

2.  Edit the MacrosLIST_CCRPC.lst file (located in the ResourceFiles folder) using a text editor. Update all file paths to indicate the Model root directory as chosen by the user.

## Installing the TransCAD Add-In

Install the GISDK program:

1.  In the main TransCAD menu, select Tools and make sure the “GIS Developer’s Kit” is enabled.

**Figure 1: GIS Developer’s Kit**
<img src="../assets/media/gisdk.png"
style="width:1.36441in;height:0.29163in" alt="GISDK_Tools.bmp" />

2.  Click the “Compile to UI” button (icon with an arrow pointing to text, see Figure 1) and navigate to the GISDK list file located: Drive:\CCRPC\ResourceFiles\MacrosLIST_CCRPC.lst

3.  This will open a “Save As” dialog box. Navigate to the CompiledUI folder (Drive:\CCRPC\ResourceFiles\CompiledUI) and save over the ccrpc_ui.dbd file in this location. (Figure 2).

**Figure 2: Compiling to UI**
<img src="../assets/media/compiling_to_ui.png"
style="width:6.5in;height:3.53681in" />

4.  Return to the TransCAD menu and Select: Tools > Setup Add-Ins and fill in the fields as shown in Figure 3. To set the “UI Database” field, the user should browse to the UI Database (“ccrpc_ui.dbd”) that was created in the previous step.

**Figure 3: Setup Add-ins**
<img src="../assets/media/setup_add_ins.png"
style="width:4.5in;height:5.60417in" />

## (Re)Installing other Versions of the Model

CCRPC model users may need to install more than one version of the model. A straightforward approach is to copy the entire root directory folder and save with a modified version name. The user can then again follow the steps outlined above only this time setting a new and distinct “Description” when setting up the add-in, and selecting the new and distinct file path for the second installations UI Database.

## Launching The Model

This section describes the general steps and procedures involved in loading and configuring CCRPC inputs using the model interface. Section 3.0 provides detailed instructions for creating a new scenario.

1.  Open the TransCAD interface by selecting Tools > Add-Ins >CCRPC (Figure 4).

**Figure 4: Model Interface**
<img src="../assets/media/model_interface.png"
style="width:4.76845in;height:7.44512in" />

2.  Select setup – this opens a new dialog box

**Figure 5: Project Scenarios Menu**
<img src="../assets/media/project_scenarios.png"
style="width:6.28125in;height:4in" />

3.  To add a new scenario, select “Copy”, which will create a new project scenario line. Enter a name for the scenario in the “Name” field and set the “Dir” (directory) button to the main directory of the scenario.

4.  Systematically step through each item in the “Steps” menu, first highlighting the item and then clicking on the “Input Files” tab (see Figure 6). Carefully check the “Status” of each input file. If any of the files have a “missing” status, then the user needs to manually identify the input file. To do so, highlight the missing file, click the “Change File” button, and navigate to the input file. Click “Ok” when all the files are listed as “Exists” in the “Status” menu. Ensure the scenarioYear parameter in the Trip Generation section is set to the target year being considered in the scenario.

5.  Click “Ok” to exit the “Project Scenarios” menu.

**Figure 6: Defining Inputs**
<img src="../assets/media/defining_inputs.png"
style="width:6.34375in;height:6.27083in" />

## Running the CCRPC Model

The CCRPC model can execute a single step or run all steps with an indefinite number of iterations until the model has converged, an equilibrium where the input assumptions are consistent with output results. Typically, users should run the model to convergence. Developers and advanced users may occasionally want to execute a single step or loop. This section describes the normal operation of the CCRPC model – running to convergence.

1.  Return to the CCRPC Model interface (see Figure 4).

2.  Click the “RUN ALL” button.

# Creating A New Scenario

This section describes the procedures involved in creating new scenarios for the CCRPC Regional Travel Model. New scenarios might feature edits to the highway network, transit system, or land use data. The "Network Manager" section steps through the process of using the Network Manager to update the master network and export a new scenario network and the "Create a New Scenario" section outlines instructions for creating a new scenario.

Table 1 presents an outline of the type of edits that might need to be made in creating a new scenario. The likelihood of the user needing to make an edit is indicated, with “high” meaning that a new scenario would likely need changes to this input, “medium” meaning that a new scenario would occasionally involve changes to this input, “low” meaning that a new scenario rarely would involve changes to this input, and “very low” meaning that new scenario would almost never involve changes to this input.

**Table 1: Physical and Structural Edits Outline**
<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 22%" />
<col style="width: 56%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Input Type</strong></th>
<th><p><strong>Update</strong></p>
<p><strong>Likelihood</strong></p></th>
<th><strong>Editing Could Corrupt Other Inputs?</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Highway Network</td>
<td>High</td>
<td>Yes. Although the transit network was designed to automatically
update for changes to the highway network, there is a small chance
highway edits could inadvertently cause a misalignment of the transit
system. After implementing a new network, the user should run the model
and check to see if any transit routes were misaligned. If so the user
should repair the transit routes, as necessary.</td>
</tr>
<tr class="even">
<td>Transit Network</td>
<td>Medium</td>
<td>No.</td>
</tr>
<tr class="odd">
<td>Land Use</td>
<td>High</td>
<td>No.</td>
</tr>
<tr class="even">
<td>TAZ Layer</td>
<td>Very Low</td>
<td>Yes. Editing the structure of the TAZ layer has a major impact on
several model systems. Such a change would require edits to the
underlying code and adjustments to the shape of all matrix inputs</td>
</tr>
</tbody>
</table>

## Network Manager

The master network contains the complete roadway network for every scenario. Roadway links that exist in the baseline model network have a value of 1 entered in the “Base” field. Links that exist only in alternative scenarios have a 0 entered for this field.

The Network Manager tool, accessed through the model GUI, allows the user to create alternative roadway networks. User-defined projects (specified in various \[projects\].bin files) control the adding, removing, and/or modifying of roadway links and nodes, while scenarios (specified in various \[scenario\].txt files) contain a list of projects. This section details the associated files and step-by-step instructions for using the network manager.

The network manager uses three primary files: master network (.dbd), project (.bin), and scenario files (.txt).

Roadway projects that may add or remove links and modify link and node attributes are stored in .bin files. The user can create future roadway projects by using the projects template, which is the Project_Template.bin file. The project files contain five fields: Project_ID, Action, ID, Field_Name, Field_Value, and Notes. The four options for the Action field are listed below in Table 2, with an example of a project file in Figure 7.

**Table 2: Project Action Commands**

| **Action** | **Description**                  |
|------------|----------------------------------|
| Add        | Adds a link to the scenario      |
| Remove     | Removes a link from the scenario |
| Modify     | Alters the indicated link field  |
| Node       | Alters the indicated node field  |

**Figure 7: Example Project .BIN File**
<img src="../assets/media/example_project_bin_file.png"
style="width:6.5in;height:3.04097in" />

Scenarios are created using text files that list out which projects (various \[project\].bin files) to be included in the scenario. Figure 8 shows an example scenario file. The names of the project files are divided by line breaks; these names must match the name of the project .bin files exactly. An optional project description can be added to the project filename if separated by a semicolon (e.g. 2025wTIP; Includes all FY 2018-2021 Front of Book TIP projects). The user can create any desirable scenario by adding or removing projects that correspond to project files. It is important to note that the Base project represents the base year network and does not correspond to a specific project file.

The \[scenario\].txt file must have a name that is 11 characters long or shorter. Using longer filenames for the scenario files will cause the model to crash.

**Figure 8: Scenario Example**
<img src="../assets/media/scenario_example.png"
style="width:6.5in;height:1.48194in" />

To run the Network Manager, follow the steps outlined below:

1.  Open the CCRPC model interface (Figure 4) and launch the Network Manager; this will open the Network Manager dialog box.

2.  In the Network Manager window (Figure 9), enter a name for the network scenario.

**Figure 9: Network Manager**
<img src="../assets/media/network_manager.png"
style="width:2.33431in;height:3.14107in" />

3.  Browse to the master network folder.

<img src="../assets/media/master_network_folder.png"
style="width:2.88403in;height:0.98819in" />

4.  Browse to the MasterNetwork_Streets.dbd and click Open.

<img src="../assets/media/master_network_streets.png"
style="width:4.70973in;height:0.69234in" />

5.  Browse to the Highway Network \[Scenario\].txt file and click Open

<img src="../assets/media/highway_network_scenario.png"
style="width:4.51887in;height:0.86663in" />

6.  Browse to the Transit Route System .rts file and click Open

<img src="../assets/media/transit_route_system.png"
style="width:4.60137in;height:0.70236in" />

7.  Navigate to the output folder, choose a name for the output network
    scenario, then click Create Network.

## Create A New Scenario

This section outlines a step-by-step set of instructions for creating a new scenario and starting a full scenario run.

1.  Create a copy of the model folder structure with a new overall folder name for the scenario under consideration.

2.  Populate the inputs folders with all necessary input files (copy from a previous scenario and replace files as necessary to represent the scenario in question)

3.  For a complete new model run, clear all former run outputs:

    a.  Delete the outputs folder.

    b.  Copy the empty outputs folder.

    c.  Rename this copy as “Outputs”.

4.  Return to the model GUI (Figure 4), navigate to “Setup” and create a new scenario by copying and modifying an existing scenario.

    a.  Set the overall parent folder path for this scenario.

    b.  Under “Steps”, go to “Trip Generation” and make sure the
        scenario year is equal to the year of your future year scenario.
        The “calibYear” should remain 2015, which is the year to which
        the base model is calibrated.

    c.  Check that all input files exist by scrolling though the various
        steps.

    d.  In the “Create Network” step, specify the streets layer if the
        alternative includes a streets network different from the 2015
        base. Click “Change File” and then select the scenario roads
        layer.

    e.  Click “Run All” to run a full scenario

# Required Model FIles

The following sections describe the files required to run the model. Refer to TransCAD documentation for further information.

## Road Network

The following network files required for the model:

- **Highway/Streets Line Layer (\[street layer\].dbd)** – This file
  describes the physical location and connectivity of the road system,
  and contains many attributes used to describe flow, for example
  classification, capacity, and one-way information.

- **Highway/Streets Node Layer** – This layer is included in the \*.dbd
  mentioned above but contains node-specific attributes like class and
  capacity.

- **Link-Type Lookup Table (LTLTable.bin)** – This table contains
  volume-delay parameters by road class. The class is specified by an
  attribute in the line layer.

- **Node-Type Lookup Table (NTLTable.bin)** – This table contains node class
  values by intersection type. The class is specified by an attribute in
  the node layer.

- **Turn Prohibitions Table (Link_TurnProhibitions.bin)** – This table
  describes base penalties or prohibitions applied to specific turning
  movements throughout the network.

- **Facility Type Penalty Table (FC_TurnProhibitions.bin)** – This table
  describes facility type –to– facility type movement penalties. The
  current implementation penalizes access to interstate ramps to prevent
  very short interstate trips.

The relationships between these files are stored in what TransCAD calls the Network file (.net). This file refers to the Highway/Streets file, the Link-Type Lookup, and the Turn Penalty Table which together describe the network, as well as details such as which attribute in the Highway/Streets layer represents Road Class or Capacity. The tables below, list the attributes of these key input files along with a description and indication if the field is manually coded by the user (User) or if it is automatically calculated by TransCAD during a model run (TransCAD).

**Figure 10: Link Type Lookup Table**

| **Field_Name** | **Comment**                                        | **Populated By** | **Units**         |
|----------------|----------------------------------------------------|------------------|-------------------|
| LinkClass      | Numberic code for link class                       | User             |                   |
| Class Type     | Description of link type                           | User             |                   |
| Speed          | Speed Limit for link class                         | User             | MPH               |
| CapPerLane     | Number of vehicles per lane for level of service F | User             | Vehicles per Lane |
| c1             | link delay paramter c1                             | User             |                   |
| c2             | link delay paramter c2                             | User             |                   |
| c3             | link delay paramter c3                             | User             |                   |
| c4             | link delay paramter c4                             | User             |                   |
| p1             | node delay parameter p1                            | User             |                   |
| p2             | node delay parameter p2                            | User             |                   |
| p3             | node delay parameter p3                            | User             |                   |
| p4             | node delay parameter p4                            | User             |                   |

**Figure 11: Node Type Lookup Table**

| **Field_Name** | **Comment**                 | **Populated By** | **Units** |
|----------------|-----------------------------|------------------|-----------|
| NodeClass      | Numeric code for node class | User             |           |
| Class Type     | Description of node type    | User             |           |

**Figure 12: Highway/street Line Layer Attributes**

| **Field_Name**           | **Comment**                                                                                                         | **Populated By** | **Units**     |
|--------------------------|---------------------------------------------------------------------------------------------------------------------|------------------|---------------|
| ID                       | Link index number created by TransCAD                                                                               | TransCAD         |               |
| Dir                      | Direction of flow with respect to link coding: two-way (0) or one-way with (1) or against (-1) the link's topology. | User             |               |
| Length                   | Length of link                                                                                                      | TransCAD         | Miles         |
| TWN_NM                   | Abreviated town name                                                                                                | User             |               |
| Class                    | Numerical code for link class                                                                                       | User             |               |
| Class_Type               | Description of link class                                                                                           | User             |               |
| Mode                     | Mode of transportation: 1 (Bus), 2 (Rail), or 3 (Auto)                                                              | User             |               |
| Walk Link                | Indication of pedestrian use: allowed (1) or prohibited (0)                                                         | User             |               |
| Drive Link               | Indication of vehicle use: allowed (1) or prohibited (0)                                                            | User             |               |
| EnhancedTransit          | Presense (1) or lack (0) of transit signal priority or BRT.                                                         | User             |               |
| Area                     | Not used                                                                                                            | User             |               |
| Speed                    | Travel speed from link type lookup table                                                                            | TransCAD         | MPH           |
| Speed_UI                 | User specified speed (overrides lookup value)                                                                       | User             | MPH           |
| Lanes                    | Travel lanes per direction (if 4 lane x-section, '2')                                                               | User             | Lanes         |
| CapPerLane               | Link capacity per lane fom link type lookup table                                                                   | TransCAD         | Vehicles/Lane |
| CapPerLane_UI            | User specified capacity per lane (overrides lookup value)                                                           | User             | Vehicles/Lane |
| Capacity                 | Total link capacity in vehicles                                                                                     | TransCAD         | Vehicles      |
| WalkTime                 | Walk time at 3 mph                                                                                                  | TransCAD         | Minutes       |
| FreeFlowTT               | Free-flow travel time                                                                                               | TransCAD         | Minutes       |
| Base                     | Master netwowrk indicatio if included (1) or excluded (0) from the base scenario network                            | User             |               |
| Toll                     | Toll value                                                                                                          | User             |  Cents        |
| Ramp                     | Indication if link is a highway ramp (1)                                                                            | User             |               |
| TAZ_Connector            | Indication if link is a TAZ connector (1)                                                                           | User             |               |
| External                 | Indication if link is an external connector (1)                                                                     | User             |               |
| Name                     | Street name                                                                                                         |                  |               |
| SelectedAreaLink         | Indication if link is part of selected area analysis (1)                                                            | User             |               |
| TruckExclusion           | Indication if link allows or prohibits trucks (Not Used)                                                            | User             |               |
| AB_AM_Count              | Calibration count in AB direction for AM peak hour                                                                  | User             | All Vehicles  |
| BA_AM_Count              | Calibration count in BA direction for AM peak hour                                                                  | User             | All Vehicles  |
| AB_AM_AutoCount          | Calibration count in AB direction for AM peak hour                                                                  | User             | Autos         |
| BA_AM_AutoCount          | Calibration count in BA direction for AM peak hour                                                                  | User             | Autos         |
| AB_AM_MedTruckCount      | Calibration count in AB direction for AM peak hour                                                                  | User             | Med Trucks    |
| BA_AM_MedTruckCount      | Calibration count in BA direction for AM peak hour                                                                  | User             | Med Trucks    |
| AB_AM_HeavyTruckCount    | Calibration count in AB direction for AM peak hour                                                                  | User             | Heavy Trucks  |
| BA_AM_HeavyTruckCount    | Calibration count in BA direction for AM peak hour                                                                  | User             | Heavy Trucks  |
| AB_PM_Count              | Calibration count in AB direction for PM peak hour                                                                  | User             | All Vehicles  |
| BA_PM_Count              | Calibration count in BA direction for PM peak hour                                                                  | User             | All Vehicles  |
| AB_PM_AutoCount          | Calibration count in AB direction for PM peak hour                                                                  | User             | Autos         |
| BA_PM_AutoCount          | Calibration count in BA direction for PM peak hour                                                                  | User             | Autos         |
| AB_PM_MedTruckCount      | Calibration count in AB direction for PM peak hour                                                                  | User             | Med Trucks    |
| BA_PM_MedTruckCount      | Calibration count in BA direction for PM peak hour                                                                  | User             | Med Trucks    |
| AB_PM_HeavyTruckCount    | Calibration count in AB direction for PM peak hour                                                                  | User             | Heavy Trucks  |
| BA_PM_HeavyTruckCount    | Calibration count in BA direction for PM peak hour                                                                  | User             | Heavy Trucks  |
| AB_DLY_Count             | Calibration count in AB direction for entire day                                                                    | User             | All Vehicles  |
| BA_DLY_Count             | Calibration count in BA direction for entire day                                                                    | User             | All Vehicles  |
| AB_DLY_AutoCount         | Calibration count in AB direction for entire day                                                                    | User             | Autos         |
| BA_DLY_AutoCount         | Calibration count in BA direction for entire day                                                                    | User             | Autos         |
| AB_DLY_MedTruckCount     | Calibration count in AB direction for entire day                                                                    | User             | Med Trucks    |
| BA_DLY_MedTruckCount     | Calibration count in BA direction for entire day                                                                    | User             | Med Trucks    |
| AB_DLY_HeavyTruckCount   | Calibration count in AB direction for entire day                                                                    | User             | Heavy Trucks  |
| BA_DLY_HeavyTruckCount   | Calibration count in BA direction for entire day                                                                    | User             | Heavy Trucks  |
| ABBA_DLY_Count           | Calibration count in both directions for entire day                                                                 | User             | All Vehicles  |
| ABBA_DLY_AutoCount       | Calibration count in both directions for entire day                                                                 | User             | Autos         |
| ABBA_DLY_MedTruckCount   | Calibration count in both directions for entire day                                                                 | User             | Med Trucks    |
| ABBA_DLY_HeavyTruckCount | Calibration count in both directions for entire day                                                                 | User             | Heavy Trucks  |
| Centroid Connector       | Indication if link is a centroid connector (1) or not (0)                                                           | User             |               |
| AB_Dir                   | Direction of flow for AB topology                                                                                   | User             |               |
| BA_Dir                   | Direction of flow for BA tobology                                                                                   | User             |               |
| Urban                    | Indication if link is in (1) or outside (0) an "urban" area                                                         | User             |               |

**Figure 13: Node Layer Attributes**

| **Field_Name**      | **Comment**                                                      | **Populated By** | **Units**      |
|---------------------|------------------------------------------------------------------|------------------|----------------|
| ID                  | Node index number created by TransCAD                            | TransCAD         |                |
| Longitude           | Longitude of node                                                | TransCAD         | Degrees x 10^6 |
| Latitude            | Latitude of node                                                 | TransCAD         | Degrees x 10^6 |
| Elevation           | Elevation of node (not used)                                     | TransCAD         |                |
| TAZ                 | Inidcation if node is a TAZ (1)                                  | User             |                |
| TAZ_Name            | TAZ identification number (1-960 internal, 10001-10017 external) | User             |                |
| External            | Indication if node is an external (1)                            | User             |                |
| Label               | Either null, "Centroid", or "External"                           | User             |                |
| Exit                | Indication of node is a highway exit (1)                         | User             |                |
| Exit_Number         | Highway Exit number                                              | User             |                |
| Class               | Node class                                                       | User             |                |
| ParkandRide         | Indication if node is a park and ride location - (not used)      | User             |                |
| Capacity            | Vehicle capacity of node                                         | User             | Vehicles/hour  |
| Town                | Abreviation of town name                                         | User             |                |
| Special Delay Link1 | Upstream node id for first stop-controlled approach              | User             |                |
| Special Delay Link2 | Upstream node id for second stop-controlled approach             | User             |                |
| Special Delay Link3 | Upstream node id for third stop-controlled approach              | User             |                |

## Trip Generation

The following land-use files inform the model trip generation.

- **TAZ Layer (“TAZ_CCRPC.dbd”)** – A geographic file that contains the
  structural detail and stores the attributes of the TAZ layer.

- **LandUse.bin** – A Fixed-Format Binary (FFB) file containing the scenario
  land-use (households and employment) for each TAZ.

- **GQuarters.bin** – A FFB file containing the number of group quarters
  dwelling units for each TAZ, and whether these are “institutional”
  (correctional facility) or “uninstititutional” (dormitory, etc.)

- **Household and Vehicle Percents by TAZ (HHandVeh_Percent.bin)** – A FFB
  file which contains the non-group quarter households categorized by
  household size and vehicle ownership.

- **Production Rate Table (ProdRates.bin)** – A FFB file that lists trip
  production rates by the joint distribution of trip purpose, household
  size, and number of vehicles..

- **Internal-External Trip Production Percentage (IXProdPercentage.bin)** –
  A FFB file containing the percentage of trips generated by the
  internal TAZs that end in external zones.

- **Internal-External/External-Internal External Trip Ends (IXXI_ExternalTripEnds.bin)** – A FFB file containing the total trip  ends in external TAZs.

- **Internal-External/External-Internal Truck Trip Ends (IXXI_Truck.bin)** –
  A FFB file containing the percent of truck trips to and from external
  TAZs.

- **External to External trips (XXTrips.mtx)** – a TransCAD matrix file
  containing trips between external zone pairs.

- **External trips growth rate (ExtTAZGR.bin)** – a FFB file containing the
  annual growth rate to be applied to external zone pair trips in future
  year scenarios.

- **Attraction model parameter files (HBW.mod, NHB.mod, HBO.mod, LCOMM.mod, MCOMM.mod, HCOMM.mod)** – contain the model parameters for attractions by trip type.

The following files are outputs of the trip generation model.

- **Productions and Attractions to and from each zone by trip type (BalancedPA.bin)** – A file showing how many trips are produced in each TAZ or are attracted to each TAZ by trip type.

## Roadway Travel Time Skims

The following files are inputs to the travel time skim model.

- **Vehicle Network Geographic File (\[street layer\].dbd)** – Similar to an ArcView shapefile, this file contains the road and intersection information for every link and node within the vehicle network.

- **TransCAD Vehicle Network (network.NET)** – This file is created by TransCAD and holds information needed to create a network for use in assignment.

- **Terminal Delay Times (TerminalTimes.bin)** – A FFB file containing the time to add to each trip based on origin and destination TAZs.

The following files are outputs of the travel time skim model.

- **Travel Time Skim with Terminal Times (\[AM\]Skims+termtimes.mtx)** – TransCAD matrix files containing congested travel time plus terminal times between each O-D pair.

## Trip Distribution

The following files are inputs to the trip distribution model.

- **Productions and Attractions to and from each zone by trip type (BalancedPA.bin)** – A file showing how many trips are produced in each TAZ or are attracted to each TAZ by trip type.

- **Travel Time Skim with Terminal Times (\[AM\]Skims+termtimes.mtx)** – Files containing the travel time (free flow travel time plus terminal times in the first iteration and congested travel time plus terminal times in each subsequent iteration) between each O-D pair.

The following files are outputs of the trip distribution model.

- **Daily Person Origin and Destination Matrix (AutoTripsInput.mtx)** – The TransCAD matrix file reporting the number of trips distributed to each O-D pair, by trip type.

## Mode Choice

The following files are inputs to the mode choice model.

- **Travel Time Skim with Terminal Times (\[AM\]Skims+termtimes.mtx)** – A file containing the travel time (free flow travel time plus terminal times in the first iteration and congested travel time plus terminal times in each subsequent iteration) between each O-D pair.

- **Transit Route System (\*.rts)** – A file which contains all of the bus and rail routes in the region.

- **Daily Person Origin and Destination Matrix (\*.mtx)** – The TransCAD matrix file reporting the number of trips distributed to each O-D pair, by trip type.

The following files are outputs of the mode choice model.

- **Nested Logit Probability Matrices by trip type (\*.mtx)** – The TransCAD matrix file containing the percentage of the trips applied to each mode.

- **Nested Logit Applied Totals Matrices by trip type (\*.mtx)** – The TransCAD matrix file containing the number of the trips derived for each mode.

- **Nested Logit Utility Matrices by trip type (\*.mtx)** – The TransCAD matrix file containing the utility of using each mode.

- **Diurnal Distribution Input Table (\*.MTX)** – A trip matrix containing the daily auto, bus and/or rail trips by trip type.

## Auto Trips by Time-of-Day

The following files are inputs to the auto trips model.

- **Daily Person Origin and Destination Matrix (autoTripsInput.mtx)** – The
  TransCAD matrix file reporting the number of person trips distributed
  to each O-D pair, by trip type.

- **Walk-Bike Ride Share (non_motorized.bin)** – A FFB file containing the
  percent of trips that are walk or bike based on the length of the trip
  in miles.

- **Transit Ride Share (transit.bin)** – A FFB file containing the percent
  of trips that utilize transit based on the length of the trip in
  miles.

- **Hourly Look-up Table (hourlyLookupTable.bin)** – A FFB file describing
  the distribution of trips by each hour of the day.

The following files are outputs of the auto trips model.

- **Hourly Vehicle Origin and Destination Matrix (odVehicleTripByHour.MTX)** – The TransCAD matrix file reporting the number of vehicle trips  distributed to each O-D pair, by trip type for each hour of the day.

## Auto Traffic Assignment

The following files are inputs to the assignment model.

- **Vehicle Network Geographic File (\[street layer\].dbd)** – The
  geographic file containing all the information necessary for a
  transportation network including: link length, number of lanes, link
  capacity, and link speed.

- **Hourly Vehicle Origin and Destination Matrix (odVehicleTripByHour.mtx)** – The TransCAD matrix file reporting the number of vehicle trips  distributed to each O-D pair, by trip type for each hour of the day.

- **Query File (“\*.qry”)** – An optional query file that may be used in assignment.

The following files are outputs of the assignment model.

- **Updated Vehicle Network showing simulated volumes and metrics (NetworkOut.dbd)** – The TransCAD geographic file with updated link volumes.

- **Final Assignment table (finalAssignmentTable.bin)** – A FFB file containing the simulated volumes and speeds, broken out by vehicle type (total, auto, medium truck, and heavy truck), along with volume to capacity ratios on each model link for each hour of the day.
