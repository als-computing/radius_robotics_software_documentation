
# Pause Scan

The user wants to pause a scan.

``` mermaid

sequenceDiagram



    actor User
    participant beamtime_ui as Beamtime UI
    participant run_manager as Run Manager
    participant qs as QueueServer
   

    activate beamtime_ui
        User ->> beamtime_ui: Click Pause Button
        beamtime_ui ->> run_manager: Send Pause
    deactivate beamtime_ui

    activate run_manager
        
       
        run_manager ->> qs: Notify QueueServer
    deactivate run_manager


```

