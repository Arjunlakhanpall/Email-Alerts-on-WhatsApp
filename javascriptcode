const nodemailer = require('nodemailer');
const { Client } = require('twilio');

const twilioAccountSid = 'your_twilio_account_sid';
const twilioAuthToken = 'your_twilio_auth_token';
const twilioPhoneNumber = 'your_twilio_phone_number';
const whatsappReceiverNumber = 'whatsapp_receiver_number';
const emailUser = 'your_email_address';
const emailPass = 'your_email_password';

const twilioClient = new Client(twilioAccountSid, twilioAuthToken);

const transporter = nodemailer.createTransport({
  service: 'YourEmailService',
  auth: {
    user: emailUser,
    pass: emailPass
  }
});

async function sendWhatsAppMessage(message) {
  try {
    await twilioClient.messages.create({
      body: message,
      from: `whatsapp:${twilioPhoneNumber}`,
      to: `whatsapp:${whatsappReceiverNumber}`
    });
  } catch (error) {
    console.error('Error sending WhatsApp message:', error);
  }
}

async function checkEmail() {
  try {
    const emails = await transporter.search(['UNSEEN']);
    emails.forEach(async email => {
      const { from, subject, text } = email;
      await sendWhatsAppMessage(`New Email Alert!\nFrom: ${from}\nSubject: ${subject}\nBody: ${text}`);
    });
  } catch (error) {
    console.error('Error checking email:', error);
  }
}

setInterval(checkEmail, 5 * 60 * 1000);
