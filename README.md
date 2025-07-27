Browser History
Helpful
In this project, let's build a Browser History app by applying the concepts we have learned till now.

Refer to the image below:

browser history output

Design Files
Click to view
Extra Small (Size < 576px) and Small (Size >= 576px)
Medium (Size >= 768px), Large (Size >= 992px) and Extra Large (Size >= 1200px) - Browser History
Medium (Size >= 768px), Large (Size >= 992px) and Extra Large (Size >= 1200px) - Empty History View
Set Up Instructions
Click to view
Download dependencies by running npm install
Start up the app using npm start
Completion Instructions
Functionality to be added

The app must have the following functionalities

Initially, the list of given history items should be displayed with a delete button for each history item.
When a non-empty value is provided in the search input, then display the history items which includes the search input irrespective of case
When the delete button of a history item is clicked, then the respective history item should be deleted from the list of history items
When a non-empty value is provided in the search input element, and no history item includes the value given in the search input, then Empty History View should be displayed
When all the history items are deleted, then Empty History View should be displayed

The App is provided with historyList. It consists of a list of historyItem objects with the following properties in each historyItem object

Key	Data Type
id	Number
timeAccessed	String
logoUrl	String
title	String
domainUrl	String
Important Note
Click to view

The following instructions are required for the tests to pass

The logoUrl in the each history item have alt as domain logo
The delete button in the history item should have the data-testid as delete
Resources
Image URLs
https://assets.ccbp.in/frontend/react-js/history-website-logo-img.png alt should be app logo
https://assets.ccbp.in/frontend/react-js/search-img.png alt should be search
https://assets.ccbp.in/frontend/react-js/delete-img.png alt should be delete
Colors

Hex: #3367d6
Hex: #2850a7
Hex: #ececec
Hex: #64748b
Hex: #f8fafc
Hex: #6697ff
Hex: #ffffff
Hex: #475569

Font-families
Roboto
Things to Keep in Mind
All components you implement should go in the src/components directory.
Don't change the component folder names as those are the files being imported into the tests.
Do not remove the pre-filled code
Want to quickly review some of the concepts you’ve been learning? Take a look at the Cheat Sheets.
