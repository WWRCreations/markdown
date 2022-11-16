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

## Chosen Improvements

Given the objectives of the company having highest priority on reliability that cars are charged when they are needed, I decided to focus on the switch.py and entity.py scripts. 

In entity.py. With more time I would check the scheduling calculations, as scheduling tends to be a common place for error in edge cases. I would add exception handling there. A concern is that the state of the pod is set to WAITING if the schedule calculations have any issues. I do not see code that fixes the issue if there is not a schedule for the day, or calculations result in a None type, beyond waiting for the next refresh cycle to trigger another calculation. Therefore in the case that scheduling fails or there is no schedule (there should always be), there could be an outcome where the device does not get charged by the needed endtime. Given more time I would write in code for enabling charging in the case that charging_allowed returns False for a long enough period, past the time when charging needs to begin to meet the end time.

The following code in switch.py waits for async_set_schedule to complete. While I am sure there is handling for exceptions within the PodPointClient code, I would look into sending backup schedules to the device (if possible) for if the wait for API connection is beyond the time when charging needs to begin.
```
async def async_turn_on(self, **kwargs):  # pylint: disable=unused-argument
        """Allow charging (clear schedule)"""
        api: PodPointClient = self.coordinator.api
        await api.async_set_schedule(enabled=False, pod=self.pod)

        await self.coordinator.async_request_refresh()
 ```
 
 The three hours went by quickly, most of it was used setting up the dev and testing environments with a few obstacles along the way and reading the code to familiarize and follow the threads. I suspect if the testing environment had worked, then I would have had more specific examples of improvements to offer. It was an interesting project, and I learned some new things.
