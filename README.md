# discover-downloaded-panos
Ansible script to discover downloaded PAN-OS versions across fleet of hosts. Useful to check that code is staged before beginning a fleet-wide upgrade.

### Requirements
* this has been tested with python-2.7
* you must have 'jq' tooling installed: `sudo apt install jq`
* the file `output.csv` must exist (empty or not) in the playbook folder. There is a task that will create this if it is missing. Contents will be replaced when the playbook is run so save it elsewhere if you want to keep a copy.

### Usage
* edit `hosts` file to include ip addresses of your ngfw to check
* edit `vars.yml` to include a valid username/password for your fleet
* run: 
``` 
ansible-playbook -i hosts ./pb_gather-firmware.yml
```
review results in output.csv

If you want to see hosts that _don't_ contain a particular version of PAN-OS, you can use
``` 
grep -v 8.0.0 output.csv
```

### Dependency notes
Dependency installation may fail due to permissions issue (read the error!)
You can fix this with:
```
pip install --user pan-python
pip install --user pandevice
pip install --user xmltodict
```

_This code is my own. Provided without warranty or affilitation with Palo Alto Networks._
