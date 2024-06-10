## Passworder

Passworder is a simple API that, given a password string and an optional algorithm, will return an encrypted string in Linux /etc/shadow format. An example call would be:
```
curl -X 'POST' \
  'http://127.0.0.1:8000/encrypt/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "cleartext": "mypassword",
  "algorithm": "SHA512",
  "random_salt": true
}'
```
..which would return the following:
``` 
{
  "shadow_string": "$6$resttrr_$mIr5dJXI71rS5PLBhuoWZMvyVOLTf3V66LBVHojSDiALab0TrvsVLfrBrakie+6Os3lsyy+WlrpsnFzYUFfayA==",
  "salt": "resttrr_"
}
```
where the shadow string can be pasted directly into the shadow file or used in a cloud-init setup. 

## Installation

To run, first install the requirements as found in the requirements.txt file. Next, from the passworder folder, use the following command:
```
C:\passworder_template\passworder> python main.py
```

The test API can be found at the listen port (as configured in the settings.yaml file), for example [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs). 

## Testing
To run the unittests, pass the following command from the passworder directory:
```
C:\passworder_template\passworder> python -m unittest discover -s ../tests
....
----------------------------------------------------------------------
Ran 4 tests in 0.000s

OK

```
