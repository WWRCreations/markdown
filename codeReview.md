# Code Review

## Dev Enviroment

The dev container task of running on port 9123 was successful, as was adding the integration for pod point. 

## Testing
As per the instructions in the README.md file in the test folder, I created and activated a venv and used the command "pip3 install -r requirements_test.txt". This documentation states that this will install homeassistant, pytest, and pytest-homeassistant-custom-component.
The following issues need to be addressed:
- the requirements_test.txt file does not include homeassistant (found in the requirements_dev.txt file) or pytest
- the install of homeassistant is unsuccessful as an error is thrown trying to install the package: python-slugify
- the install of pytest-homeassistant-custom-component=0.5.14 is unsuccessful as an error is thrown trying to install the package: voluptuous
- this file and documentation should include the install of podpointclient which is in the requirements.txt file

## Chosen Improvement 

Given the objectives of the company having highest priority on reliability that cars are charged when they are needed, I decided to focus on the test_sensor.py and test_switch.py scripts. Without the ability to run the tests, I am limited to reading through the code. 

My Contribution:
