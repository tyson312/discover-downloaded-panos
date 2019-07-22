# discover-downloaded-panos
Ansible script to discover downloaded PAN-OS versions across fleet of hosts

### requirements
These are listed in the playbook as well but:
* you must have 'jq' tooling installed: sudo apt install jq
* the file output.csv must exist (empty or not) in the playbook folder

### usage
* edit hosts file to include ip addresses of your ngfw to check
* edit vars.yml to include a valid username/password for your floeet
* run: 
``` 
ansible-playbook -i hosts ./pb_gather-firmware.yml
```
review results in output.csv

If you want to see hosts that _don't_ contain a particular version of PAN-OS, you can use
``` 
grep -v 8.0.0 output.csv
```

### dependency notes
Dependency installation may fail due to permissions issue (read the error!)
You can fix this with 
```
pip install --user pan-python
pip install --user pandevice
pip install --user xmltodict
```

