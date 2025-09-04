# TrelloDownloadManager
* TrelloDownloadManager is an application used to generate csv files based on data exported from Trello boards.
* It is referred to as the application
* The application reads all relevant information from one or more Trello Boards into a dataset and writes relevant data from this dataset into some csv output files.
* The csv output files contain information about all boards, board lists, cards, labels, check items and custom fields in the specified Trello boards.

## Terminology
* Board: Represents a Trello Board, the board contains board lists with cards.
* Board List: Cards on a board are organized into board lists. Alle the board lists on the board are shown horizontally after each other
* Card: Cards are placed on a board and organized into board lists. Cards are shown vertically after each other in the board list.
* Labels: A board defines what labels are avaliable. Any of the labels defined on the board can be applied to any card on the board. Labels have a specific text and color and are used set a characteristic on a card
* Check Items: Any card can have checklists with check items. Any check item have a name and can be either checked or unchecked.
* Custom Fields: A board defines what custom fields are available. Each card can assign a value to a custom field.
* Board Action: Whenever a user makes a change on a Trello board a board action is created and stored on the board (These are not visible on the board). These function as a kind of history of all the changes applied to the board and might be used to store a history of all changes to the board.

## Running the application
To be able to run the application you must install .NET 9.0 on the computer. You can donload the .NET 9.0 here: https://dotnet.microsoft.com/en-us/download

The program file and other required files can be found here: https://specialsport.sharepoint.com/sites/IFELspecialsport/Flles%20filer/Forms/AllItems.aspx?id=%2Fsites%2FIFELspecialsport%2FFlles%20filer%2FIT%20%26%20DATA%2FDataindsamling%20og%20analyser%2FDatawarehouse%2C%20opstart&p=true&ct=1756898697453&or=Teams%2DHL&ga=1&LOF=1

Finding the applcation folder:
* There is a zip file named: Code.zip
* Unpack this to a folder on your computer.
* Navigate in the unpacked folder to the application folder that can be found at this relative path: \TrelloDownloadManager\bin\Debug\net9.0

The easiest way to use the program is to:
* Copy the application folder into a folder to your computer.
* Create an input folder somewhere on your computer, you might call it "Input"
  * You can now add Trello Export files to the input folder
* Create an output folder somewhere on your computer, you might call it "Output"
  * This is where the csv output files will be generated
* Open the configuration file (the file named config.json) in a text editor
  * You must change the "InputFolder" to the location of the newly created input folder on your computer
  * You must change the "OutputFolder" to the location of the newly created output folder on your computer
* You can start the application by double clicking the program file in Windows Explorer.
  * The program file is named TrelloDownloadManager and is of type "Program"
  * The program will only run successfully if the folder containing the program file also contains the files
    *  TrelloDownloadManager.dll
    *  TrelloDownloadManager.runtimconfig
    *  config.json
* Now the program will start and you will se a black console window on the screen.
  * In the console window you can see the progress of the application.
  * The console windows will also show if there are any errors or warnings while running the program
  * When the program has finished it will show the line "Finished" in the console window and you can click in the console window and press Enter to close down the program (or just close it with the cross in the upper right corner, like you close any other console application)
  * If there are no errors then the application has read the Trello Export files in the input folder and created csv output files on the output folder.
    * Note that if there are no Trello Export files i the input folder then there will be no lines (except the header lines) in the csv output files.
   
NOTE: When running the application it will require full access to the files in the output folder. When running the application it will try to delete the csv files and create them again. If you have the file open in another program such as Excel, this might put a lock on the files to that the application cannot delete them and will not work.

## Trello Export Files
The application collect information from one or more Trello Boards using Trello Export files into a dataset.
You must add a Trello Export file to the input folder for each board you want includedd in the dataset.

You generate the Trello Export file for a Trello board by:
* Opening the board (in your browser)
* Click on the three dots in the upper right corner of the Trello Board to open the menu
* Select "Print, export, and share" from the menu
* Select "Export as JSON" from the dialog
* The Trello Export files are now downloaded to your donwload folder
* You must move or copy the Trello Export files to the input folder for the application to use them.

## Output Csv Output Files
* The application generates csv output files, containing information from the dataset
* Each csv output file represents an entity in Trello. Note that if you have multiple boards in the dataset the Csv files show aggregated data from all the boards.

### Custom fields
* Some csv output files show custom fields (one column per custom field), this includes any custom field that is defined on any of the boards in the dataset.
* The header contains the name of the custom field (usualy "ID"), usualy prefixed with ("CF_").
* Columns for custom fields are sorted alphabetically based on custom field name.
* On the board.csv file the values in custom field columns the id of the custom field on the specified board, or empty if the board has no custom field matching the name. * On the card.csv file the values in custom field columns contain the value of the custom field on the given card, or empty of the field is not defined for the given card.
* In Special Sport all the boards have either one custom field (named ID, that represents the Donorfy ID) or no custom fields.

### Labels
* Some Csv output files show labels (one column per label), this includes any label that is defined on any of the boards in the dataset.
* The header contain the name of the label, ususally prefixed with ("LBL_).
* Columns for labels are sorted alphabetically based on label name.
* On the board.csv and cards.csv file the values in label colums are the id of the label in the specified board, or empty if the board has no label matching the name.

### Check items
* Some Csv output files show check items (one column per check item name), this includes any check item name that is defined on any check list on any of the cards in the dataset.
* The header contain the name of the check item, ususaly prefixed with ("CI_).
* Columns for check items are sorted alphabetically based on check item name.
* On the cards.csv the values in the label coluns is either "complete" if the check item i checked, "incomplete" if the check item is cleared or empty if the card has no check item matching the name.

### board.csv
* Contains one row for each board in the dataset
* Columns are created for general board information such as board name and the board id
* Columns are created for custom fields that are defined in any of the boards. 
* Columns are created for all labels on any of the boards.
* Columns are created for all boardlists on the boards

### boardlist.csv
* Contains one row for each board list on any of the boards in the dataset.
* Columns are created for general board list information such as board name, board list name, board list id

You can use the boardlist.csv to:
* See how many boards contain a board list with a given name.
* See whether any board lists are closed on one board but not on others
* See if the same name is used for boardlist no all the boards.

### cards.csv
* Contains one row for each card on any of the boards in the dataset.
* Columns are created for general card information such as board name, board list name, card name, card id and closed
* Columns are created for all labels defined on any of the boards in the dataset
* Columns are created for all check items defined defined on any of the boards in the dataset

### labels.csv
* Contains one row for each label defined on any of the boards in the dataset.
* Colunms are created for general label information such as board name, label name and color

### boardactions.csv
* Contains one row for each board action defined on any of the boards in the dataset.
* Note that each board only contains the latest 1000 actions performed on the board
* Columns are created for general action information such as type, id and date.
* Columns are added for additional data defined on any of the board actions. Since there are a lot of posibilities for different additional data there are a lot of additional data columns.

## Configuring the application in the config.json file
You can configure the application in the config.json file.

Here is a list of elements that you can specify to change the behaviour of the application:
* InputFolder: Specifies the folder where the Trello Export files should be read from
* OutputFolder: Specifies the folder where the Csv output files should be written to
* LabelColumnHeaderPrefix: All column headers for Labels are prefixed with this text
* ListColumnHeaderPrefix: All column headers for Board Lists are prefixed with this text
* CustomFieldPrefix: All column headers for Custom Fields are prefixed with this text
* CheckItemPrefix: All column headers for Check Items are prefixed with this text
* BoardSettings: Contains information regarding configuration of the 'Board' Csv output file. Mainly which columns to show
* BoardListSettings: Contains information regarding configuration of the 'BoardList' Csv output file. Mainly which columns to show
* CardSettings: Contains information regarding configuration of the 'Card' Csv output file. Mainly which columns to show
* LabelSettings: Contains information regarding configuration of the 'Label' Csv output file. Mainly which columns to show
* BoardActionSettings: Contains information regarding configuration of the 'BoardAction' Csv output file. Mainly which columns to show
* IncludedFields: Indicates which fields should be included as columns.
* IncludedDataFields: Indicates which data fields should be included as columns.
* IncludeLabels: Indicates whether labels should be included as columns
* IncludeLists: Indicates whether board lists should be included as columns
* IncludeCheckItems: Indicates whether check items should be included as columns

NOTE:
* You should never change the structure of the file, only the values of the individual elements (the part after the colon).
* If the structure is changed the application will fail to run properly.

 Here is an example of a full config.json file
   
 >{
    "InputFolder" : "C:\\TrelloFolders\\Input",
    "OutputFolder" : "C:\\TrelloFolders\\Output",
    "LabelColumnHeaderPrefix" : "LBL_",
    "ListColumnHeaderPrefix" : "LST_",
    "CustomFieldPrefix" : "CF_",
    "CheckItemPrefix" : "CI_",
    "BoardSettings" : {        
        "IncludedFields" : ["name", "id", "desc", "closed", "url", "dateLastActivity"],
        "IncludeLabels" : true,
        "IncludeLists" : true
    },
    "BoardListSettings" : {
        "IncludedFields" : ["name", "id", "closed"]
    }, 
    "CardSettings" : {
        "IncludedFields" : ["name", "desc", "idList", "closed", "isTemplate"],
        "IncludeLabels" : true,
        "IncludeCheckItems" : true
    },
    "LabelSettings" : {
        "IncludedFields" : ["name", "id", "idBoard", "color"]
    },
    "BoardActionSettings" : {
        "IncludedFields" : ["type", "id", "date"],
        "IncludedDataFields" : ["data_attachment_id", "data_attachment_name", "data_attachment_previewUrl", "data_attachment_previewUrl2x", "data_attachment_url", "data_board_id", "data_board_name", "data_board_shortLink", "data_card_closed", "data_card_cover_brightness", "data_card_cover_color", "data_card_cover_idAttachment", "data_card_cover_idUploadedBackground", "data_card_cover_manualCoverAttachment", "data_card_cover_plugin", "data_card_cover_size", "data_card_dateClosed", "data_card_dateCompleted", "data_card_desc", "data_card_due", "data_card_dueComplete", "data_card_dueReminder", "data_card_id", "data_card_idAttachmentCover", "data_card_idLabels", "data_card_idList", "data_card_idShort", "data_card_name", "data_card_pos", "data_card_shortLink", "data_card_start", "data_card_template", "data_cardSource_id", "data_cardSource_idShort", "data_cardSource_name", "data_cardSource_shortLink", "data_checkItem_id", "data_checkItem_name", "data_checkItem_state", "data_checklist_id", "data_checklist_name", "data_customField_id", "data_customField_name", "data_customField_type", "data_customFieldItem_id", "data_customFieldItem_idCustomField", "data_customFieldItem_idModel", "data_customFieldItem_idValue", "data_customFieldItem_modelType", "data_customFieldItem_value_number", "data_dateLastEdited", "data_deactivated", "data_fromCopy", "data_idCard", "data_idMember", "data_idMemberAdded", "data_list_id", "data_list_name", "data_list_pos", "data_listAfter_id", "data_listAfter_name", "data_listBefore_id", "data_listBefore_name", "data_member_id", "data_member_name", "data_memberType", "data_old_closed", "data_old_cover_brightness", "data_old_cover_color", "data_old_cover_idAttachment", "data_old_cover_idUploadedBackground", "data_old_cover_manualCoverAttachment", "data_old_cover_plugin", "data_old_cover_size", "data_old_desc", "data_old_due", "data_old_dueComplete", "data_old_dueReminder", "data_old_idAttachmentCover", "data_old_idLabels", "data_old_idList", "data_old_name", "data_old_pos", "data_old_start", "data_old_template", "data_old_value_number", "data_text"]
    }
}

## Using the Output Csv Files in Excel
* You can use Excel to get an overview of the data in the csv files.
* It is easiest to open an Empty Excel workboook and add one worksheet for each csv file.
* To import the csv data into a worksheet you use the "Data" menu item in the menu and then select "Hent Data" -> "Fra Fil" -> "Fra tekst/CSV".
* In the "Importer Data" dialog you select the csv file and click "Importer
* In the next dialog Excel shows a preview of the imported data. Her you must make sure the the delimiter ("afgrænser") is set to "Semikolon".
* If data looks right and columns are giver right names (based on the first line in the csv file), then you can just click import and the worksheet is updated.
* If the column headers are not given the right names, then you need to click "Transformer Data" and then click "Brug den første række som overskrifter" and then "Luk og Indlæs" to import the data.

When data is imported to Excel you can set filters.
Examples are filters  thIe you can set filters so that you only see rows related to a specific board, or rows for at specific card or maybe see all the car


## Working with the the application from Visual Studio Code
* You can run the application from Visaul Studio Code (VS Code)
* You must first install Visual VS Code on you computer.
* If you want to use Git this must also be installed
* Open a Windows Console (or PowerShell)
* In the console navigate to the folder containing the source code, you must navigate to the folder where the file "TrelloDownloadManager.sln" i located.
* Then in the consol write: code .
* Remember to include the "." it will open VS Code in your current folder
* In the primary side panel (the panel to the left) select "Explorer" to select the Explorer panel.
* You should now be able to see the code in the "Code" section of the Explorer panel.
* Make sure you can see the file "TrelloDownloadManager.sln" (along with other files and folders) in the root of the "Code" section.
* In VS Code you need to install the extension "C# Dev Kit", after this is done then you should have a "Solution Explorer" section in the Explorer, that has a tree containing a "TrelloDownloadManager" root node (the soultion file) with a "TrelloDownloadManager" child node (the project file).
* You can now run the application by clicking F5 or select the "Run and Debug" in the primary panel and from here that the application.
* You can also make changes to the code. The code has a Git repository so if you have Git installed on your computer you can see changes and commit them from the "Source Control" available in the primary side panel.




