# Code Refactoring Readme

Thank you for giving me the opportunity.

- Arrays have been replaced with empty brackets, making it easier to read the code.
- The if condition has been replaced with a ternary operator at the top of the method, to execute the where statement only if the variable has data.
- A suggestion has been made to move the Curl code to a separate helper function in a new CurlHelper file. This would make it easier to call and reuse the method.

Better code
	Using a repository in Laravel is better
	In repository a method called `isNeedToDelayPush` has been added to immediately return false and stop further execution. 

Good but suggessions

	In addition, it is suggested that for conditions where we check if a variable is set, we use ternary operators instead of if-else statements. 

	To use the Curl code, the fields are first converted to JSON format using `json_encode`, and then passed to `curlPost` function in the CurlHelper file. The response is logged using the `$logger` object. 
		$headers = array('Content-Type: application/json', $onesignalRestAuthKey);
		$response = curlPost("https://onesignal.com/api/v1/notifications", $fields, $headers);
		$logger->addInfo('Push send for job ' . $job_id . ' curl answer', [$response]);

	Overall, these changes to make the code more efficient, readable, and maintainable.

Suggessions
	we will move notification method to helper file sendPushNotificationToSpecificUsers if we need to send notification then we will call helper directly
	if we use que jobs it will reduse request time sendSMSNotificationToTranslator for this
	we have to create config file for storing role ids like if we have 3 type for role like
- student 
- teacher
- admin

	return [
		'student' => [
			'id' => 1,
		],
		'teacher' => [
			'id' => 2,
		],
		'admin' => [
			'id' => 3,
		],
		// other roles
	];

	$studentId = config('role.student.id');
	Add bulk insert for create // createOrUpdate