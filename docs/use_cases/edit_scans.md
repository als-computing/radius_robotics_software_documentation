
# Edit Scans

Once scans have been loaded and displayed in the browser, the user may make changes to the order or values of the scans.

``` mermaid

sequenceDiagram



    actor User
    participant beamtime_ui as Beamtime UI
    participant run_manager as Run Manager
    participant qs as QueueServer


    activate beamtime_ui
        User ->> beamtime_ui: Make Edits in UI, click Send
        beamtime_ui ->> run_manager: Send Changes
    deactivate beamtime_ui
   
    activate run_manager

            alt Run Manager accepts changes
                run_manager ->> run_manager: Calculate Queue Changes
              
            else Run Manager changes
                run_manager ->> beamtime_ui: Notify Rejection
                beamtime_ui ->> beamtime_ui: Display issues
            end

       
    deactivate run_manager


```



notes
- persist sample changes to scicat
- remove queue modify here, save for later
- no modification of queue serer until scan starting