The starter code on the task sheets contains seeded faults. They are the same in Round 1 and Round 2 of each scenario, so both rounds stay comparable (GP3). They make fault finding (D4) observable.

| Scenario | Fault | Symptom students see | Round 1 location | Round 2 location |
|---|---|---|---|---|
| A | Sorting compares the wrong way (`v < SORT_THRESHOLD` instead of `>`) | Bright parts go to lane B, dark parts to lane A | Sorting station | Sorting station, shows up later in the counting message |
| B | Actuator uses the wrong rule | R1 the warning LED comes on with the fan (`FAN_ON_C` instead of `WARN_C`). R2 the pump also runs in the OK band (`m != WET` instead of `m == DRY`) | Last lines of loop() | actuate() |
| C | Detection re-arms while the car is still there (`nearSamples` instead of `farSamples`) | One car that stays in front of a sensor is counted again and again | Two places in loop(), entry and exit | One place in laneEvent(), module Detection |
| C | Exit check allows a negative count (`>= 0` instead of `> 0`) | Count goes to -1 when a car leaves an empty garage | Exit block in loop() | registerExit(), module Counting |
| C | Yellow has no upper limit | Yellow and red are on together when the garage is full | Yellow LED line in loop() | showState(), module Display |

## What to watch in Scenario C

In Round 1 the team has to search the whole shared program. In Round 2 the owner searches in their own module. Note how a fault is found, by whom, and whether the search is global or local.
