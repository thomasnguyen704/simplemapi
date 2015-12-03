This zip file contains the following files:

1. SwapMain.cpp
2. SwapMain.h
3. Swap.cpp
4. Swap.h

SwapMain.cpp is the main controling program file.  It is responsible for displaying a menu to the user and interpreting the commands given by the user.  The code in this file is written specifically for a console application, but because it makes calls into a separate module that implements functionality using a user defined class, a windows style application could be easily substituted as the main controller of the application.

Swap.cpp is the implementation of an application class that provides the basic functionality required by the menu presented in the main control module.

This messaging application is a Simple MAPI client.  It implements the following features:

	- Present the user with a menu
	- Logon to messaging system
	- Select a recipient/Get e-mail address
	- Enter e-mail address/Get recipient
	- Get details of recipient
	- Send mail message to recipient using defaul UI
	- Send mail message to recipient with no user interface
	- Send mail message with an attachment
	- Create a new message
	- List messages in the Inbox
	- Read next unread message
	- Log off of the messagin system
	- Exit the client
	- Refresh the menu


The following features will not be discussed in this document because the code to implement them is trivial and not related to MAPI at all:

	- Present the user with a menu
	- Exit the client 
	- Refresh the menu

Logon to messaging system:
Prompts the user for a profile name. If it can find the profile name in the list of profiles, it will log the user on to the messaging system.  If it cannot find the profile entered by the user in the list of profiles, the user will be asked to cancel the operation or choose from and existing list.

Select a recipient/Get e-mail address:
The user is prompted with an address book list. When an entry is chosen from this list, the method allocates a buffer and stuffs the buffer with the e-mail address of the recipient chosen in the list. The buffer must be released by the caller of this method.

Enter e-mail address/Get recipient:
The user is prompted to type an e-mail address. When a valid e-mail name is entered and found in the address book, the method allocates storage for a buffer and stuffs the buffer with the display name of the e-mail alias. The buffer allocated in this method must be released by the caller.

Get details of recipient:
The user is prompted to type an e-mail address. When a valid e-mail address is entered and found in the address book, the user is presented a "details" page filled with information specific to the e-mail address entered by the user.

Send mail message to recipient using defaul UI:
The user is prompted with the default "Compose Note" form. When the message has been given a recipient to send to and the send button is pressed, the intended recipient will get the message.

Send mail message to recipient with no user interface:
The user is prompted for the intended recipient. After a valid recipient is entered, a hard coded message is sent to the intended recipient.

Send mail message with an attachment:
The user is prompted for the intended recipient. After a valid recipient is entered, the user is prompted for the file and path of a file to attach. The file name must be the 8.3 representation of the file to attach. The path name must be in the following format: "c:\windows\" (Note: the trailing backspace is mandatory). A message is then sent to the intended recipient.

Create a new message:
A new message is automatically created in the inbox of the user's default message store.

List messages in the Inbox:
The user is presented with a list of the messages in the user's default message store inbox.

Read next unread message:
The user is presented with the contents of the next unread message in the default message store inbox.

Log off of the messaging system:
The session handle is released and the user is logged off of the messaging system. No MAPI specific menu options will be available until the user requests to be logged back on to the messaging system. The application remains running until the user chooses to exit the application. If the user elects to exit the application without first logging off, the session is terminated in an orderly fashion and then the application will exit.
