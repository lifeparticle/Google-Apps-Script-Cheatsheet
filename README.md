```gs
function onFormSubmit(e) {
  var response = e.range;
  var rRow = response.getRow()
  console.log("test" + rRow);
  var email = e.namedValues["Email Address"][0]
  console.log("email" + email);
  sendEmailConfirmation(email, rRow);
}

function sendEmailConfirmation(email, rRow) {
  var subject = "Your Form Submission Confirmation";
  var message = "Thank you for your submission! Your response has been recorded in row number: " + rRow;
  MailApp.sendEmail(email, subject, message);
}

function authorize() {
  SpreadsheetApp.getActiveSpreadsheet();
  MailApp.sendEmail(Session.getActiveUser().getEmail(), "Authorization Test", "This is a test email to trigger authorization.");
}
```
