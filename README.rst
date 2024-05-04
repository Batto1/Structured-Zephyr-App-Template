.. _structured_zephyr_app_template:

Structured Zephyr Application Template
###########

Overview
********

This is a template for applications being developed on `Zephyr platform <https://github.com/zephyrproject-rtos/zephyr>`_ that showcases somewhat more advanced file structuring that can be useful for achievening a more intiutive and better handled software files such that foldering and categorising the files itself doesn't create any overhead on the development. Furthermore it's aimed that development files can be easily explored in every stage of project by any familiar or unfamiliar developer working on the project. 


File Structuring Principles
********

Based on the guidelines I provided in "Some Arguments" section, below were my principles for creating such a file structure:
- Every necessary file gathered together and separated from the others are called modules. Modules have every necessary one files such as source and header files along with their related configuration files, README and other documents.
- Modules should have their own necessary files (CMakeList, Kconfig, README and other documents) beside them. Parent folder's CMakeList and Kconfig should have the control to include them or not such that modules are easily included or excluded. With this, we distribute the control of file hierarchy to modules themselves rather than a central place ('central place' such that having only one CMakeList or Kconfig or prj.conf). 
- All modules that make the logic, define configuration, configure and help build and describe the module and make of the application originate from one folder called **'app'**.
- Every configuration selection that change (i.e. dynamic by selecting based on some specific preference) and that can't directly be included when some module is activated originate from one folder called **'conf'**
- Every document that doesn't explain a module itself originate from one folder called **'doc'**
- For the sake of easier accessibility to a module's file it's chosen to categorize less for some modules such as 'main_processor' under 'app>hw_modules' although it could be in the 'onboard' folder.
- A CMakeLists.txt file exists at the root of the application directory. It's function is to make necessary central configurations and add "app" as subdirectory so that other CMakeLists.txt on the folder tree can be included.  
- A Kconfig files exists at the root of the application directory. It's function is to make necessary central configurations and add "app" as subdirectory so that other Kconfig on the folder tree can be included.  
- A prj.conf file exist although all production configuration should reside in 'conf'. But it's kept for trying out configurations switfly and quickly directing a developer that's not familiar with the file structure to the 'conf' file to find configurations he's looking for, with the help of comment lines written inside.,
- A 'boards' folder exists optionally if the application will run on a custom board. Application is built to run in this board. Files exist for an example custom board, you should make appropriate changes to this folder's files according to your own custom board if it exists. (Note: 'Board' term is the Zephyr's choice and I referred to it as 'main processor' in wherever it's applicable.)


Background
********

Modularised, readable, scalable, maintainable software projects generally require meticulous foldering and categorization of files. Applications developed on Zephyr RTOS is not any different and Zephyr platform also requires special attention on different kinds of files other than source files such as: 
- configuration files (KConfig)
- configuration selection files (.conf)
- devicetree related files (.dts, .dtsi, .yaml etc.)
- CMake files (CMakeLists.txt)

Also, depending on the application requirements and preferences of the development team, there can exist other kinds folders and files such as:
- doc (document folder which can include all kinds of files for documenting)
- README files
- version control files and folders (.git, .gitignore etc.)

Dealing with all these kinds of different files are a work by itself and not dealing with them properly create other kinds of overhead while working, too thus, this exemplary template is created.

How to Start Using This Template?
=============

Here are the steps:
- Clone this repo
- Examine the file structure and be familiar with it
- Make necessary changes to structure according to your project
- Stick to the structuring as you keep adding files, folders, configurations etc.


Building and Running
=============

This template can be used with any :ref:`supported board <boards>` on Zephyr RTOS platform. Check `Zephyr documents <https://docs.zephyrproject.org/latest/develop/index.html>`_ for building instructions.

Some Arguments
=============

We humans can better understand concepts, do work, keep information in our memory and solve problems better when information is somewhat categorised and their distinctions are explored from other information. While this is absolutely necessary for almost every information that we need to work with, too much of it also methaporically paralyzes us from working because there is practical limit to our working memory. Think of some document or textbook that has 6 levels of subchapters. The categorisation itself becomes the information and it can overwhelm us if we need to do work quickly. Or think of a thick book that only has a title. This time, amount of sheer monolithic information cause the overwhelm and we try to categorize it by ourself.

So, for the biological brain you need to modularise information by its distinctions from the other related information under some subject and you need to add relevant categorizing information over some information but not do it 'too much' or 'too little'. This 'too much' or 'too little' depends on so many things including the depth of the information and personal preferences and experiences such that it actually is impossible to base it on some universal rules (although maybe some guidelines can be viable). But we humans, when we work together have to agree on them to work together and understand each other. A concrete example is division of labor. We humans spend years and years in school to properly understand some information in some small section area of vast information to be able to produce practical work. But sometimes these small sections grow and has to be divided into some other smaller sections. Think of the computer science, what used to be only computer science is now divided into AI science, LLM science, Machine Learning science etc. If it wasn't divided it'd be too much information, if it was divided into more, it wouldn't be practical, for now. So from all these explored concepts and understanding, let's try to produce some guidelines for humans for how we should manipulate and work with information such that it makes sense for most: 
- **The information of categorisation itself shouldn't be larger than or irrelevant to the information in the categories.** (If you're giving a simple cooking recipe, you don't need to explain it in 30 steps rather than 5, or don't need to categorize the steps if any intricate cooking technique isn't necessary)
- **The information of categorisation itself shouldn't be smaller than the information in the categories such that the informations are missed.** (If your dish has different intricate cooking techniques that needs proper care on each of them, you can't just explain it in a couple steps that are following each other)
- **If everyone knows more about the subject and 'language' of work, both the categorisation information and the information itself isn't overwhelming to them.** ("Prepare a pasta dough according to Chef X's recipe" sentence is not overwhelming to someone that know and prepared that dough before but a new cook needs more instructions and time)
- **If everyone knows more about the subject and 'language' of work, further development of categorisational information and the information itself develops more advanced practical work.** (You can change something or add something from your experience to some recipe you know to make it better or even transform, but someone that doesn't even know the recipe can't)
- **Language inherently assumes some level of common understanding of information although it can change on a personal and time basis, and language is not sufficient to directly represent an idea if the rules of the words and symbols are not strictly defined on mathematical basis, if such thing is even possible** (Since your ingridients are different from the recipe's author, even you'd call your dish the same name, it won't be and taste like the author's or even your other dishes made with the same recipe. Even worse, maybe you won't even understand the recipe partially or fully and won't even know that you understood it wrong or right.)

With these arguments, the file structuring principles I provided were created.

