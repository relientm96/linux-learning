# Root Folder

Below is a list of sub file systems under root directory:

```
├── bin : Binary storage, that is executable from any parent path
├── dev : For external devices connected
├── etc : Stores configuration files
├── home : Contains home directory for the user
├── lib : Essential Shared Libraries
├── media : Removable media, such as inserting a CD, will create a directory under `media/`
├── mnt : Temporary mount points. Used to mount partitions.
├── opt : Optional packages
├── proc : Store process folders
├── root : Home directory for the root user
├── run : Filesystem for tools needing to mount early
├── sbin : Binaries for administrative tools (such as package managers, ip stuff)
├── srv : Used by services, wanting a single tree for writable data/scripts
├── sys : Stores driver information
├── tmp : Temporary file storage, deleted whenever system restarts
├── usr : User binaries and read only data
├── var : Writable usr/ directory, mostly contains log files from processes
```