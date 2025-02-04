
# Load Scan

``` mermaid

sequenceDiagram



    actor User
    participant beamtime_ui as Beamtime UI
    participant run_manager as Run Manager
    participant qs as QueueServer
    participant robot as Robot
    participant ericware as 7.3.3 Labview
    participant bcs as BCS Labview
    participant adaptive as Adaptive
    participant scicat as SciCat

    User ->> beamtime_ui: Click Start Loading Button
    
    activate run_manager
        beamtime_ui ->> run_manager: get sample info
        
        run_manager ->> robot: scan the tray
        robot -->> run_manager: bar/sample information
        run_manager ->> scicat: get sample info
        scicat -->> run_manager: sample info
        run_manager ->> run_manager: calculate scans
        run_manager ->> beamtime_ui: new scan info
        
        note right of run_manager: See Edit Scans
    deactivate run_manager
    

```

