# Using Lambda function to extend a deep learning project with AWS DeepLens


## Scenario
Based on the previous tutorial, now we will guide you to capture events for further processing and extend the pre-trained model functionality using AWS Lambda. You will first capture the events from AWS DeepLens model, and put them in the queue ready for further processing.


## Prerequisites
>The workshop’s region will be in ‘N.Virginia’

>An AWS DeepLens device is necessary for this tutorial. You can buy AWS DeepLens here: https://www.amazon.com/dp/B075Y3CK37


## Lab tutorial
### Verify your AWS DeepLens project
1.1.	On the service menu, click **AWS DeepLens**.

1.2.	Click the hamburger icon on the left side, choose **Devices**. 

1.3.	Click your AWS DeepLens decive, and make sure there are a project working on it.

1.4.	Scroll down in your device screen, and copy the MQTT topic name in the bottom, it should be look like **$aws/things/deeplens_xxxxxxxxxxx/infer**.

1.5.	Go to **Greengrass** console.

1.6.	Select the **Test** section on the left side.

1.7.	Paste the MQTT topic name into the Subscription topic input field.

1.8.	Select **Subscribe** to topic.

1.9.    Verify that you can see the project output from the device. You can also verify the output stream with browser which was taught in previous tutorial.



### Create a Lambda function

2.1.	In Greengrass console, select the **Act** section on the left side.

2.2.	Click **Create a rule**.

2.3.	In the name field, give a specific name to your rule, for example, **object-detection-rule**.

2.4.	Scroll down to the Action section, and click **Add action**.

2.5.	Select **Send a message to an SQS queue**.

2.6.	Click **Configure action**.

2.7.	In Queue name section, click **Create a new resource**.

2.8.	It will open a new page of SQS management console. In Create New Queue, give a specific queue name, for example **object_detection_output**.

2.9.	Click **Quick Create Queue**.

2.10.	Go back to the previous page, and click **refresh icon**.

2.11.	Then select the queue that you’ve just created.

2.12.	Click **Create a new role**.

2.13.	Give a specific name to the new role, for example **object-detection-queue-role**.

2.14.	Click **Create a new role**.

2.15.	Click the **refresh icon** for the IAM role list.

2.16.	Select the IAM role that you’ve just created.

2.17.	Click **Add action**.

2.18.	In the Attribute, type *.

2.19.	In the Topic filter, paste your device’s MQTT topic.

2.20.	Scroll down, and click **Create rule**.



### View SQS queue from your device

3.1.	Go to **Simple Queue Service** console.

3.2.	Select the queue that you’ve just created.

3.3.	Click **Queue Actions**.

3.4.	Select **View/Delete Messages**.

3.5.	A window will pop up, and click **Start Polling for messages**.

3.6.	If your model is connecting and your device is running, you should be able to view the output from the project.



## Conclusion

Congratulations! You now have learned how to:
* Create a Lambda function for extending the DeepLens model.
* View the extended function for capturing the events.

## Next Level
Building an AWS DeepLens Project using Amazon SageMaker

