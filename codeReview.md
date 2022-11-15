# Code Review

## Dev Enviroment

First I created a virtual machine with Ubuntu, installed Docker and VSC and the containers extension.
Forked, cloned, and opened the repo in a container to get used to the development environment and running the code.

The code is meant to:


## Testing
As per the instructions in the README.md file in the test folder, I created and activated a venv and used the command "pip3 install -r requirements_test.txt". This documentation states that this will install homeassistant, pytest, and pytest-homeassistant-custom-component.
The following issues need to be addressed:
- the requirements_test.txt file does not include homeassistant (found in the requirements_dev.txt file) or pytest
- the install of homeassistant is unsuccessful as an error is thrown trying to install the package: python-slugify
- the install of pytest-homeassistant-custom-component=0.5.14 is unsuccessful as an error is thrown trying to install the package: voluptuous
- this file and documentation should include the install of podpointclient which is in the requirements.txt file

Without working testing code, it was more difficult to approach looking for parts of the code that need improvement.

Testing showed:

Recommended Improvements:

## Chosen Improvement 

Chosen improvement for focus and reasoning:

My Contribution:
