## Brief
"Main processor" is referred as the IC (integrated circuit) such as a MCU, SoC or SiP which the application is built for to program it. 

### Digression
The phrase 'main processor' is chosen. Other namings such as central IC, main computer etc. were considered but goal for the naming was that user intuitively could understand this was the HW (hardware) module at the heart of the application. 'central' word could be a good choice since it conveys the meaning that there can be components around the central component but folder naming 'central_IC' doesn't seem to be accomplishing the naming goal and 'central_processor' seems to remind more of CPU (central processing unit) thus 'main_processor' is chosen. 
If there was a proper and more common word other than 'processor' or 'IC' that could describe MCUs, SoCs or SiPs altogether, that'd be used.

## Portability of Codetion but this is not in this file's scope.
Code is portable since drivers for the HW are same. The interface between communicating HW may change depending on the applica

## Parent Folder Name
main_processor

## Properties Of The Parent Folder 
The parent folder should contain this README file, some software (SW) files related with main processor, and any other necessary and related files. Files should be appropriately categorized and foldered as required. For example, code related to the IC itself or the common code for the IC series can be separated (for example, as nRF52 and nRF52840 for nRF52840).

## Note
By the definition, this file's parent folder can be a sub-folder of 'onboard' folder but they are made sibling folders to avoid nesting folders too much. Also, it's considered that the main_processor folder should be more easily found and accessible in the parent folder structure.
