
# Start Scans

The user kicks off the scans.

``` mermaid

sequenceDiagram



    actor User
    participant beamtime_ui as Beamtime UI
    participant run_manager as Run Manager
    participant qs as QueueServer
    participant broker as MessageBroker
    participant robot as Robot
    participant ericware as 7.3.3 Labview
    participant bcs as BCS Labview
    participant adaptive as Adaptive
    participant scicat as SciCat


    activate beamtime_ui
        User ->> beamtime_ui: Click Start Button
        beamtime_ui ->> run_manager: Send Start
    deactivate beamtime_ui

    activate run_manager
        run_manager ->> qs: Notify QueueServer
    deactivate run_manager
    activate qs
        par Do Run
            qs ->> robot: do stuff
        and 
            qs ->> ericware: do stuff
        and
            qs ->> bcs: do stuff
        and
            qs ->> broker: run documents
        and
            broker ->> adaptive: run documents
        end
    deactivate qs
 
```

