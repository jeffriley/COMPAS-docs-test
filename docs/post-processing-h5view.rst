h5view.py
=========

This program displays summary, header, and content information for specified COMPAS ``HDF5`` file(s). It's fairly rudimetary - the 
``HDF5`` package provides ``h5dump`` and ``h5ls`` which have far more options than this program - but this program is somewhat 
COMPAS aware.

Detailed information regarding ``h5view.py`` functionality is documented at the top of the `h5view.py` source file.


h5view.py usage
---------------

::

    h5view.py [-h] [-f FILENAME_FILTER] [-r [RECURSION_DEPTH]] [-S] [-H]
                   [-C [CONTENTS]] [-s] [-x EXCLUDE_GROUP [EXCLUDE_GROUP ...]]
                   [-V SEED_LIST [SEED_LIST ...]]
                   input [input ...]

    HDF5 file content viewer.

    positional arguments:
      input
        input directory and/or file name(s)

    optional arguments:
      -h, --help
        show this help message and exit
      -f FILENAME_FILTER, --filter FILENAME_FILTER
        input filename filter (default = *)
      -r [RECURSION_DEPTH], --recursive [RECURSION_DEPTH]
        recursion depth (default is no recursion)
      -S, --summary
        display summary output for HDF5 file (default is not to displat summary)
      -H, --headers
        display file headers for HDF5 file (default is not to display headers)
      -C [CONTENTS], --contents [CONTENTS]
        display file contents for HDF5 file: argument is number of entries (+ve from top, -ve
        from bottom) (default is not to display contents)
      -s, --stop-on-error
        stop all copying if an error occurs (default is skip to next file and continue)
      -x EXCLUDE_GROUP [EXCLUDE_GROUP ...], --exclude EXCLUDE_GROUP [EXCLUDE_GROUP ...]
        list of input groups to be excluded (default is all groups will be copied)
      -V SEED_LIST [SEED_LIST ...], --seeds SEED_LIST [SEED_LIST ...]
        list of seeds to be printed (for content printing) (default is print all seeds)


Example
-------

Typing::

    python3 h5view.py compas-output-file.h5
    
will result in summary output of the ``HDF5`` file `compas-output-file.h5` that looks something like this::

    Summary of HDF5 file /d/compas/h5out.h5
    =======================================

    File size    : 2.1520 GB
    Last modified: 2021-07-26 16:25:12.928401

    COMPAS Filename              Columns   Entries   Unique SEEDs
    --------------------------   -------   -------   ------------
    Run_Details                      346        30
    BSE_Common_Envelopes              73    582485         476514
    BSE_Double_Compact_Objects        12      8725           8725
    BSE_RLOF                          34   2997481         536332
    BSE_Supernovae                    32    103000          87162
    BSE_Switch_Log                    13   7472234         956623
    BSE_System_Parameters             33   1050000        1050000


Other ``h5view.py`` options (listed above) display headers and file contents.

