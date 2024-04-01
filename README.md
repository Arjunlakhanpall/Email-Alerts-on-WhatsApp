Just a simple code 
1. **Dependencies**: The code requires the `nodemailer` and `twilio` modules. These modules are used for sending emails and WhatsApp messages, respectively.
2. **Configuration**: It includes configuration variables for Twilio (Twilio account SID, authentication token, phone number), WhatsApp (receiver number), email credentials (username, password), and the email service.
3. **Twilio Client Initialization**: It initializes a Twilio client using the provided account SID and authentication token.
4. **Nodemailer Transporter Initialization**: It creates a Nodemailer transporter using the specified email service and credentials.
5. **Function to Send WhatsApp Message**: This function sends a WhatsApp message using the Twilio client. It takes a message as input and sends it to the specified WhatsApp receiver number.
6. **Function to Check Email**: This function checks for unread emails using the Nodemailer transporter's `search` method. If there are unread emails, it iterates over them and sends a WhatsApp alert for each one.
7. **Interval Execution**: The `setInterval` function is used to repeatedly call the `checkEmail` function at a specified interval (every 5 minutes in this case).
