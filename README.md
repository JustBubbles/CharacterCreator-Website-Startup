#StartUp Specification
##Elevator Pitch
  For my start up I want to create a website that will help users come up with and flush out character ideas for roleplaying games, writing, and/or original characters (OCs), and share them with others. This website will provide users with templates and tools---such as a random backstory prompt generator, a random character archetype generator, and a random name generator---to help create more complete and flushed out character ideas and backgrounds. This website will allow users to create an account, store their creations, and allow others to view their characters by enabling the proper setting in the character sheet, meaning a user can choose which of their characters are public and which are private.  

##Key Features:
- <ins>**Character creator**</ins>: Users will be able to create and save their characters and character concepts
- <ins>**Character creation tools**</ins>: Users will have multiple tools to help in character creation such as a name generator, backstory prompt generator, and a character archetype generator.
- <ins>**Character browser**</ins>: Users will be able to browse and look at other users' creations.

##Representation of Technologies
- <ins>**HTML**</ins>: I will have 5 pages. One will be for login and account creation. Another will be a homepage that will allow the user to choose between browsing public characters, creating their own character, and the idea generator tools. The other three pages will be those three options.
- <ins>**CSS**</ins>: I will use CSS to create a well formatted website that looks good on multiple screen sizes. I will also add multiple simple animations to the character creation page to make it more engaging. 
- <ins>**React**</ins>: I will use React to provide login/logout information, account creation, swap between different pieces of character information in the character creator, and swap between users' public characters when in the browse page.
- <ins>**Service**</ins>: Backend service with endpoints for:
    - Register, login, and log out users
    - Storage and retieval of user's saved characters
    - Storage and retrieval of public characters.
    - Option to generate random character names using the [https://lukewh.com/blog/fantasy-name-generator-api](https://lukewh.com/blog/fantasy-name-generator-api) api.
- <ins>**Database**</ins>: Store users, authentication information, user information, character information, and public characters information.
- <ins>**WebSocket**</ins>: When a user saves their character as public, it will be added to the browse page and public characters database.

##Application Sketch
###Homepage
<img width="1206" height="747" alt="Homepage" src="https://github.com/user-attachments/assets/364f478a-6ae3-4e31-b824-c6ca8dbf478b" />

###Login Screen
<img width="1187" height="731" alt="LoginPage" src="https://github.com/user-attachments/assets/cb802954-a16c-4281-a419-fb5ef99d74e2" />

###Character Creation
<img width="1207" height="733" alt="CharacterCreatorPage" src="https://github.com/user-attachments/assets/489776e8-c485-4422-a54b-f1be255aa29e" />



