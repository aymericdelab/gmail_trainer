# gmail_trainer
Pypi package to send an email to yourself whenever the training of your model has finished. 

You can install the package using:
<pre><code>pip install gmail-trainer</code></pre>

The first step is to go to this website to enable the Gmail API:
https://developers.google.com/gmail/api/quickstart/python

<img src="https://i.imgur.com/vtkWlnc.png">

Once you have enabled the API, a credentials.json file gets downloaded. Put it in your working directory and execute this code:
<pre><code>from gmail_trainer import SendMail
gmail = SendMail()
service = gmail.create_credentials()
</code></pre>

A chrome page opens up and asks you to allow the API to access sending mails. Once its done a token.pickle file containing the access codes is created in your working directory. You can even copy that file to other directories to enable gmail-trainer for other projects as well.

Now that you have your pickle file ready and are about to start training a long deep neural network, you can add this code snippet at the end of your training. The message content could contain the performance of your algorithm. As long as its a String.

<pre><code>
message = gmail.CreateMessage(address='youremailaddress@gmail.com',
                              msgPlain='Your message containing your algorithm performance as a String. This will be the body of the email.')
result = gmail.send_msg(service, message)
</code></pre>

Now you will get an email once the training is done ! Which you can check on your phone. This is ideal if you want to take some time off your laptop screen.
