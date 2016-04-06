# Chopper simulation

This repository contains a Virtual device for simulation of choppers at ESS. Choppers at ESS are abstracted in such a way that
all of them are exposed via the same interface, regardless of manufacturer. The behavior of this abstraction layer can
be modelled as a finite state machine.

The docs-directory contains an `fsm`-file (created using the program [qfsm](http://qfsm.sourceforge.net/)) which describes
the state machine. While this is still work in progress, it gives an idea of how the choppers are going to operate internally.

## Python module

The state machine that is sketched in the document mentioned above is implemented in Python using the
[Fysom](https://pypi.python.org/pypi/fysom) library, which can be installed via the requirements file in simulation directory:

```
pip install -r simulation/requirements.txt
```

## EPICS interface

The simulator is exposed to channel access, using the [pcaspy](https://pypi.python.org/pypi/pcaspy)-module. Depending on the level
of simulation there may be different PVs available to control the simulated chopper. At a minimum, the following PVs will be
exposed:

| PV  | Description  | Unit | Access |
|---|---|---|---|---|
| speed  |  Current rotation speed of the chopper disc. | Hz  | Read |
| speed:sp  | Speed setpoint.  | Hz | Read/Write |
| phase  |  Current phase of the chopper disc. | Degree | Read |
| phase:sp  |  Phase setpoint | Degree | Read/Write |

