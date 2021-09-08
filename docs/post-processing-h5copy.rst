h5copy.py
=========

This program copies ``HDF5`` file(s) to a designated output HDF5 file.  If the output file is an existing ``HDF5`` file, the 
user can  specify whether the existing content should be erased before copying begins, or whether the copied data should be 
appended to the existing data. If multiple files are given as input files, the resultant ``HDF5`` file is the concatenation
of the input files.


Some nomenclature
-----------------

A COMPAS output file (e.g. ``BSE_System_Parameters``, ``BSE_RLOF``, etc.) maps to an ``HDF5 GROUP``, where the group name is 
the name of the COMPAS output file.

A column in a COMPAS output file (e.g. ``SEED``, ``Mass(1)``, ``Radius(2)``, etc.) maps to an ``HDF5 DATASET``, where the 
dataset name is the column heading string.

COMPAS column datatype strings are encoded in the dataset meta-details (dataset.dtype).
COMPAS column units strings are attached to ``HDF5`` datasets as attributes.

Detailed information regarding ``h5copy.py`` functionality is documented at the top of the `h5copy.py` source file.


h5copy.py usage
---------------

::

    h5copy.py [-h] [-b BUFFER_SIZE] [-c CHUNK_SIZE] [-e] [-f FILENAME_FILTER]
                   [-o OUTPUT_FILENAME] [-r [RECURSION_DEPTH]] [-s]
                   [-x EXCLUDE_GROUP [EXCLUDE_GROUP ...]]
                   input [input ...]

    HDF5 file copier.

    positional arguments:
      input
        input directory and/or file name(s)

    optional arguments:
      -h, --help
        show this help message and exit
      -b BUFFER_SIZE, --buffer-size BUFFER_SIZE
        IO buffer size (number of HDF5 chunks, default = 10)
      -c CHUNK_SIZE, --chunk-size CHUNK_SIZE
        HDF5 output file dataset chunk size (default = 100000)
      -e, --erase-output
        erase existing output file before copying input files (default = False)
      -f FILENAME_FILTER, --filter FILENAME_FILTER
        input filename filter (default = *)
      -o OUTPUT_FILENAME, --output OUTPUT_FILENAME
        output file name (default = h5out.h5)
      -r [RECURSION_DEPTH], --recursive [RECURSION_DEPTH]
        recursion depth (default is no recursion)
      -s, --stop-on-error
        stop all copying if an error occurs (default is skip to next file and continue)
      -x EXCLUDE_GROUP [EXCLUDE_GROUP ...], --exclude EXCLUDE_GROUP [EXCLUDE_GROUP ...]
        list of input groups to be excluded (default is all groups will be copied)


    Note: if the -x option is specified, it should be specified at the end of the options 
          list (i.e. the list of input files can't follow the -x option or the list of input 
          files will be subsumed by the list of groups to be excluded)


