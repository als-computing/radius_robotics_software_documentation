
# Edit Scans

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

    activate beamtime_ui
        User ->> beamtime_ui: Make Edits in UI, click Send
        beamtime_ui ->> run_manager: Send Changes
    deactivate beamtime_ui
   
    activate run_manager

            alt Run Manager accepts changes
                run_manager ->> run_manager: Calculate Queue Changes
                 run_manager ->> qs: Modify Queue
            else Run Manager changes
                run_manager ->> beamtime_ui: Notify Rejection
                beamtime_ui ->> beamtime_ui: Display issues
            end

       
    deactivate run_manager


```

