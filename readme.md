# PEST Procedure 

This script allows users to implement the PEST procedure (Macmillan and Creelman, 2005, p282-283) to determine the appropriate stimulus intensity per trial.



## Parameters

This table lists the parameters associated with this plugin. Parameters can be left unspecified if the default value is acceptable.

|Parameter|Type|Default Value| Descripton|
|---------|----|-------------|-----------|
|`starting_intensity`|numeric|0.7|The starting intensity of the stimulus.|
|`down_threshold`|numeric|3|The number of trials in a row the participant gets correct before a step down is taken.  <br/>(E.g., If this is set to 3, then 3 correct responses in a row causes the stimulus intensity to take a step down.)|
|`up_threshold`|numeric|1|The number of trials in a row the participant gets incorrect before a step up is taken. <br/>(E.g., If this is set to 1, then every incorrect response causes the stimulus intensity take a step up.)|
|`upper_intensity_limit`|numeric|1|The highest intensity of the stimulus for this PEST procedure. Any intensity level that is supposed to be higher than this limit is set to this limit.|
|`lower_intensity_limit`|numeric|0|The lowest intensity of the stimulus for this PEST procedure. Any intensity level that is supposed to be lower than this limit is set to this limit.|
|`starting_step_size`|numeric|0.32|The starting step size for this PEST procedure.|
|`min_step_size`|numeric|0.01|The smallest step size for this PEST procedure. Any step size that is supposed to be smaller than this step size is set to this step size.|
|`max_step_size`|numeric|0.32|The largest step size for this PEST procedure. Any step size that is supposed to be larger than this step size is set to this step size.|



## Example

#### Setting up the parameters of the PEST procedure (i.e., the staircase):
```javascript
//Create a JS Object to hold the parameters
var myParameters = {
	starting_intensity: 3,
	upper_intensity_limit: 5,
	lower_intensity_limit: 0.2,
	starting_step_size: 1,
	min_step_size: 0.0625,
	max_step_size: 2
};
```

#### Create the staircase object:
```javascript
//Create and initialize a new pest object with the parameter object passed in as an argument
var myPest =  new pest(myParameters);

//Parameters of myPest are now initialized, and you can use its staircase() method
```

#### Use the staircase:
```javascript
//In every trial, call the staircase() method of the pest object with the correctness of the previous trial (boolean) passed in as an argument.

var intensity_for_this_trial = myPest.staircase(correctness_of_previous_trial);

// ^ The argument for the first trial will be ignored, so it is safe to use the same function to determine the correctness_of_previous_trial for all your trials.

```
