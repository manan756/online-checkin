# online-checkin
Task #1: Writing Test Scenarios

|    Test Scenarios  for Online Check-In Service    |                                                                                                                        |                                                                          |                                                                                   |                    |                   |                             |                            |
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------|-------------------|-----------------------------|----------------------------|
|    Test Case ID                                   |    Description                                                                                                         |    Expected Output                                                       |    Actual Output                                                                  |    Status (Dev)    |    Status (QA)    |    Dev Comments (if any)    |    QA Comments (if any)    |
|    TC-001                                         |    Verify that upon selecting suit button, check-in/out   dates, No. of guests and cancellation options are visible    |    All related fields showing correct data                               |    All fields showing related data correctly                                      |                    |    Pass           |                             |                            |
|    TC-002                                         |    Upon selecting required dates the no. of   nights and total payable including tax calculated correctly              |    No. of nights and rent  including VAT is calculated correctly         |    No. of nights and rent is calculated   correctly                               |                    |    Pass           |                             |                            |
|    TC-003                                         |    Verify that on clicking book now button the page   with title “ Confirm and Pay” and contacts is visible            |    All fields are mandatory to fill                                      |    All fields are mandatory                                                       |                    |    Pass           |                             |                            |
|    TC-004                                         |    Verify that in“ Confirm and Pay ” section   card number and CVC are verified                                        |    Error messages should be shown on wrong   entering card no. or CVC    |    Error messages are shown on wrong entry                                        |                    |    Pass           |                             |                            |
|    TC-005                                         |    Verify that in  “Contacts ” section valid email and phone   number are entered                                      |    Both email and phone number should be verified                        |    Email is verified but phone number country code i.e   +49  is not mandatory    |                    |    Fail           |                             |                            |

Task #2: Finding Defects

|    Online Check-In  Defects    |                                                                                                             |                                                                               |                                                                     |                    |                   |                             |                                |   |
|--------------------------------|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|---------------------------------------------------------------------|--------------------|-------------------|-----------------------------|--------------------------------|---|
|    Test Case ID                |    Description                                                                                              |    Expected Output                                                            |    Actual Output                                                    |    Status (Dev)    |    Status (QA)    |    Dev Comments (if any)    |    QA Comments (if any)        |   |
|    TC-001                      |    Upon selecting “ online check-in ”  page all user guiding information should be   displayed correctly    |    All information is displayed correctly                                     |    Description under “ online check-in ” is not   understandable    |                    |    Fail           |                             |    Screenshot   is attached    |   |
|    TC-002                      |    Upon selecting “ online check-in ”  page information displayed in German or in English   completely      |    Upon selecting “DE” option whole page   should be translated in Deutsch    |    Upon selecting “DE” option nothing is   translated in Deutsch    |                    |    Fail           |                             |    Screenshot is attached      |   |
|     

All given description should be user understandable under selected language          |                                                                                                            |                                                                               |                                                                     |                    |                   |                             |                                |   |

![1](https://user-images.githubusercontent.com/60622187/73882836-a1767780-4884-11ea-8c40-5021ce0f0fa1.png)

All given description should be displayed according to user selected language

![2](https://user-images.githubusercontent.com/60622187/73882924-cec32580-4884-11ea-870a-b835da5825fe.png)

Task #3: Defect Reporting

|    Defect ID number    |    BT-001                                                                                                     |
|------------------------|---------------------------------------------------------------------------------------------------------------|
|    Name                |    Text - Unable to translate or read text                                                                    |
|    Reporter            |    Abdul                                                                                                      |
|    Submit Date         |    05/02/2020                                                                                                 |
|    Summary             |    When I retrieve my booking I’m unable to understand   the description provided on booking details page.    |
|    URL                 |    https://limehome-qa-task.herokuapp.com/registrationForm/abdul@gmail/abdul                                  |
|    Screenshot          |    Attached for reference                                                                                     |
|    Platform            |    limehome online check-in                                                                                   |
|    Operating System    |     W/10                                                                                                      |
|    Browser             |    Chrome 79                                                                                                  |
|    Severity            |    Major                                                                                                      |
|    Assigned to         |    /                                                                                                          |
|    Priority            |    High                           


Description
When retrieving the exciting booking, the description under “Personal details”, “Trip” and “Customer Support” is shown in default text, it seems page is still under construction.

Steps to reproduce
> User adds last name.
> User enters booking reference number and presses submit.
> On page with title “Your booking details” the text under “Personal details” is not readable.
> The text under “Trip” is not readable.
> The text under “Customer Support” is not readable.
> After entering all relevant details when user presses submit, the text under “Thank you” is not readable.

Expected result
All details and text should be shown according to user selected language (EN or DE).

Actual result
The text shown is not translated in English or Deutsch.

ScreenShots
                                                                            |
![3](https://user-images.githubusercontent.com/60622187/73883067-1649b180-4885-11ea-8a41-d6d2d5585bd4.png)
![4](https://user-images.githubusercontent.com/60622187/73883100-2497cd80-4885-11ea-806d-cd5aa2397ebf.png)

Task #4: e2e Automation 

describe('Testing online check-in service', function() {

    it('verify title', function() {
      cy.visit('https://limehome-qa-task.herokuapp.com/')
      cy.contains('Online check-in')
      cy.get('#mat-input-0')
      .type('abdul')// last name, this value is to compare
      cy.get('#mat-input-1').type('abdul756@gmail.com')// booking refrence
      cy.get('button.mat-button').click()//submit
      cy.focused().click() 
      cy.contains('Your booking details')// Next page with booking details
      cy.get('#mat-input-3').should('have.value','abdul')//last name, compare with this
      cy.get('#mat-input-4').type('01/02/1993')// DOB
      cy.get('#mat-select-2').click()// Trip type
      cy.contains("Business").click()// selecting business type trip
      cy.get('button.mat-button').click()//final submit

      
      
    })
    
  })
