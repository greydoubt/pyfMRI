# pyfMRI
python fMRI controller / hypervisor


loads and interacting with Functional Mock-Up Units (FMUs) both for Model Exchange and Co-Simulation, pre-compiled dynamic models compliant with the Functional Mock-Up Interfaces (FMIs) for fMRI and other scanning devices, then applies functional programming layers (FFT etc) 

goals:

roblox integratioin

QNX support for hypervisors

using: 
https://jmodelica.org/pyfmi/pyfmi.html#module-pyfmi.fmi_algorithm_drivers


ncp    --
    Number of communication points.
    Default: '500'

initialize --
    If set to True, the initializing algorithm defined in the FMU model
    is invoked, otherwise it is assumed the user have manually invoked
    model.initialize()
    Default is True.
    
stop_time_defined --
    If set to True, the model cannot be computed past the set final_time,
    even in a continuation run. This is only applicable when initialize
    is set to True. For more information, see the FMI specification.
    Default False.

write_scaled_result --
    Set this parameter to True to write the result to file without
    taking scaling into account. If the value of scaled is False,
    then the variable scaling factors of the model are used to
    reproduced the unscaled variable values.
    Default: False

result_file_name --
    Specifies the name of the file where the simulation result is
    written. Setting this option to an empty string results in a default
    file name that is based on the name of the model class.
    Default: Empty string

result_handling --
    Specifies how the result should be handled. Either stored to
    file (txt or binary) or stored in memory. One can also use a 
    custom handler.
    Available options: "file", "binary", "memory", "csv", "custom"
    Default: "binary"

result_handler --
    The handler for the result. Depending on the option in
    result_handling this either defaults to ResultHandlerFile
    or ResultHandlerMemory. If result_handling custom is chosen
    This MUST be provided.
    Default: None

return_result --
    Determines if the simulation result should be returned or 
    not. If set to False, the simulation result is not loaded
    into memory after the simulation finishes.
    Default: True
    
time_limit --
    Specifies an upper bound on the time allowed for the 
    integration to be completed. The time limit is specified 
    in seconds. Note that the time limit is only checked after
    a completed step. This means that if a do step takes a lot
    of time, the execution will not stop at exactly the time
    limit.
    Default: none

filter --
    A filter for choosing which variables to actually store
    result for. The syntax can be found in
    http://en.wikipedia.org/wiki/Glob_%28programming%29 . An
    example is filter = "*der" , stor all variables ending with
    'der'. Can also be a list.
    Default: None
