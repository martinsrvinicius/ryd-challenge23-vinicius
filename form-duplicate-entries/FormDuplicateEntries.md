Duplicated Entries!
===================

In a former project we had a contact form.
In our production database we have found multiple entries of the same user.

Please describe shortly your approach in debugging this situation and name 2-3 different possible reasons for this kind of "bug".
For each option describe how we could fix this behavior.


## Applicant response 
NAME: VINICIUS RICARDO MARTINS

It might occur when no input validation is applied or no feedback to the user is provided so he does several attemps to insert the data. 

One possible solution would be a pop up confirmation on the first entry of the data so the user might feel safe.

Another problem is no database confirmation  for a possible previous user account registration. 
A solution would be a sql query with "DISTINCT" command search for a match data on the email or user name fields, for exemple. If the search is positive the user should receive a feedback that says the user already exists.

A bug also would be a character entry mismatch. The user could have inserted some special character which would pass the sql validation search. A solution would be to convert the user input to utf-8 and guarantee the data input on the database is correct.