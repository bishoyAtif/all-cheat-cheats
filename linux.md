## Using the command line

- ### Intro ###
    - A directory is simply another name for a folder. When we’re working at the command line, we will refer to folders as directories.
    - A computer’s files and folders are structured like a tree. At the beginning is a root directory that ultimately branches out to many other folders (each with the potential to contain more folders and files). What we’re doing when we navigate our computer’s file system is effectively walking up and down certain branches of this figurative tree structure.
    - When we enter a command line interface, we should think of ourselves as being present at a particular location on the computer — meaning that we’re currently inside some directory.
    - By default, when we open the shell, we’ll be starting at the Home folder on our computer, indicated by a tilde (```~```) symbol.
    - We’ll notice in the shell that a cursor appears after a dollar sign (```$```). This is where we will enter commands.
---
- ### pwd ###
    - The first command that will be useful for us is called ```pwd```, which stands for “print working directory.” When we type this command and hit the ```RETURN``` or ```ENTER``` key on our keyboards, the shell will respond by outputting what’s called an absolute path to where we are in the computer’s file structure system.
    ```console
        ~ $ pwd
        /home/ubuntu
    ```
    - By default, when we open the shell, we’ll be starting in our computer’s Home directory, displayed in abbreviated form by a tilde (```~```) symbol in the command prompt. The path to your own computer's home directory may differ depending on your username and operating system.
---
- ### ls ###
    - To see the contents of a directory, we can use the ```ls``` (or “list”) command, as shown below.
    ```console
        ~ $ ls
        Desktop Documents Downloads Library Movies Music Pictures Public
    ```
    - If you want to see all files in a directory (including hidden ones), you can add a flag ```ls -a``` to list “all” of the contents present. Hidden files will appear with a . preceding their names.
---
- ### xdg-open ###
    - To open a file or a directory
    ```console
        ~ $ open Downloads
    ```
    This will bring up a window displaying (through a GUI) the contents of the ```Downloads``` directory.
    - You can use the ```TAB``` key on your keyboard to autocomplete file and directory names that reside in your current (or “working”) directory. You may notice that autocompleting a directory name will add a trailing slash (/).
    - To open the current (working) directory, you can type the following command:
    ```console
        ~ $ open .
    ```
    The ```.``` in this context indicates your current (working) directory.
---
- ### cd ###
    - Recall that when you open the shell, you start out at your computer’s Home directory, abbreviated in the prompt as ```~```. If you want to move from your Home directory into another, you can use the ```cd``` (or “change directory”) command.
    - To move into a different directory, you provide that new directory’s name.
    ```console
        ~ $ cd Desktop
        ~/Desktop $
    ```
    This command will move you from the Home directory into the Desktop directory.
    - Notice that, when our current (working) directory changed from the Home (or ~) directory to the Desktop directory, the prompt text also changed from ```~ $``` to ```~/Desktop $```, That’s because the text before the $ in the prompt is, by default, set up to display an absolute path to your current location in the computer’s file structure. This can be a helpful reminder of where you are if you’re ever traversing deep into the computer’s file structure. (Alternatively, you can always use the ```pwd``` command to print out your working directory!)
    - Once you’ve changed directories, you can easily access files and folders contained in that new directory. So if you used ```ls``` command now displays the contents of the Desktop rather than the contents of the Home directory.
    - Just as we can move deeper into our computer’s file structure, we can also move back up to a higher-level folder.
    ```console
        ~/Desktop $ cd ..
    ```
    Using ```..``` indicates the parent directory, or the one above our working directory.
    - Finally, no matter where we are, if we simply type in the ```cd``` command without any destination directory, we’ll just be taken to our ```home``` directory.
---
- ### mkdir ###
    - The ```mkdir``` command is used to make a new directory with the name that we provide. For example, if you’re in the ```Desktop``` directory and want to create an ```animals``` directory in that location, you'd type the following command:
    ```console
        ~/Desktop $ mkdir animals
    ```
    - If you wanted to then create a ```rodents``` directory inside of ```animals```, you could do either of the following (starting from the ```Desktop```):
    use ```cd``` to move into ```animals```, and then type: ```mkdir rodents```, or
    simply run the command ```mkdir animals/rodents``` from your current directory.
    - You can also use mkdir to create multiple directories at once. To do so, you provide a list of directory names separated by spaces. For example, to create three directories with names of marsupials, cloven_hoofed_animals, and carnivores inside the animals directory, you can use the following command:
    ```console
        ~/Desktop/animals $ mkdir marsupials cloven_hoofed_animals carnivores
    ```
    - You should avoid using spaces in directory and file names (hence the underscores in ```cloven_hoofed_animals```). If this is unavoidable — perhaps if you encounter a previously created file or directory name with a space in it — you can insert what’s called an escape (```\```) character before the space to tell the shell how to properly interpret the spaces in that file name, e.g. ```mkdir cloven\ hoofed\ animals```.
---
- ### touch ###
    - #### Creating a file in your working directory ####
        - Until this point, you’ve most likely created and saved files on your computer by using a particular application — for example, creating a .docx file in Microsoft Word, a .pdf file in Adobe Acrobat, or an .html file in a text editor. At the command line, you can create a file in your working directory with a single command called ```touch```. The ```touch``` command creates a new (empty) file with the name and file extension that you provide. For example, if you’re in the ```Desktop``` directory and want to create a file named ```first_file.txt``` in that location, you can type the following:
        ```console
            ~/Desktop $ touch first_file.txt
        ```
        The inclusion of the file extension (```.txt``` in this case) is crucial because it sets the file type. Running the above command and then listing the contents of the ```Desktop``` directory confirms that a text file with the name ```first_file.txt``` was indeed created.

    - #### Creating a file in a directory other than the working directory ####
        - You can also use the ```touch``` command to create a file that resides in a directory other than your working directory. To do this, you must prepend to your file name the path leading to your desired destination. For instance, given the following file structure, you can create from your Desktop working directory a text file named ```capybara.txt``` that resides several layers deeper than your working directory.
        - Example file structure:<br>
        Home (or ~) directory → Desktop directory → animals directory → rodents directory → capybara.txt file.<br>
        To do so, you’d execute the following command:
        ```console
            ~/Desktop $ touch animals/rodents/capybara.txt
        ```

    - #### Creating multiple files ####
        - You can create multiple files with the ```touch``` command by providing multiple file names (including any appropriate prepended paths), separated by spaces. <br> 
        For example, the code below will create two files:
            - one file named kangaroo.txt residing at: ```~``` → ```Desktop``` → ```animals``` → ```marsupials```.
            - and another file named giraffe.txt residing at: ```~``` → ```Desktop``` → ```animals``` → ```cloven_hoofed_animals```
        - ```console
            ~/Desktop $ touch animals/marsupials/kangaroo.txt animals/cloven_hoofed_animals/giraffe.txt
        ```

    - #### Creating different file types ####
        - Lastly, it’s important to note that you aren’t restricted to creating only text files with the ```touch``` command. you can create any file type you please. For instance, the following command will create (in the Desktop working directory) a Python file with the name test.py:
        ```console
            ~/Desktop $  test.py
        ```
---
- ### rm command ###
    - #### Removing files ####
        - You can use the ```rm``` (or “remove”) command to delete specified files. Please note that **THIS DELETION IS PERMANENT** — it cannot be reversed. Only use rm if you are sure you want to delete something.
        - Let’s consider an example. If you want to remove a file named first_file.txt that resides in the Desktop directory, you can run the following command:
        ```console
            ~/Desktop $ rm first_file.txt
        ```
        - Deleting multiple files is accomplished by providing a list of file names, separated by spaces.
        ```console
            $ rm apples.txt carrots.txt fruits.txt
        ```

    - #### Removing directories ####
        - ##### Using ```rmdir``` #####
            - The rmdir command can be used to delete directories, but it’s important to note that it can only remove completely empty directories.
            - For example, you can use mkdir to create a directory called ```cats``` inside the ```Desktop``` directory. Because  is just an empty directory (nothing has been added to it), you can successfully use the ```rmdir``` command to remove the ```cats``` directory
        - ##### Using ```rm -r``` #####
            - However, if you try to run ```rmdir``` on a directory that is not empty, you’ll receive an error message. For example, if you create a cats directory and then add files to it (e.g. munchkin.txt and tabby.rb), you won’t be able to use rmdir to remove the cats directory.
            - A potential solution would involve first emptying the directory’s contents one file at a time (using the ```rm``` command you learned above) and then using ```rmdir``` to remove the emptied directory, but this can be inefficient if a directory contains many files.
            - To remove a directory, you can add something called a flag or option to the ```rm``` command. Flags provide additional execution instructions. They are included after the command name but before the argument. Flags are indicated by letters following a dash (```-```) symbol. The complete command we’ll use in this section is ```rm -r```, where ```r``` stands for recursive.
            - **CAUTION:** Before you proceed, you should know that recursive deletion means deleting all contents of a directory — that includes its files, its sub-directories, any files within those sub-directories, and so on. Furthermore, deletion with ```rm -r``` is a permanent action. You can easily and irreversibly delete great numbers of files with this one command.
            - Let’s consider an example. If you want to remove a non-empty directory named cats that lives in your Desktop directory, you could use the following command:
            ```console
                ~/Desktop $ rm -r cats
            ```
            - If you’d like to be asked to confirm the deletion of individual items contained in a directory, you can add the interactive (```-i```) flag to your command, either by combining it with the ```-r``` flag (e.g. ```rm -ri```) or by adding it separately (e.g. ```rm -r -i```). For instance, if the cats directory happened to contain two files (```file_1.txt``` and ```file_2.txt```) and four sub-directories (calico, persian, scottish_fold, and siamese).<br>
            - You could use the following command to delete the cats directory after confirming the deletion of its several contents:
            ```console
                ~/Desktop $ rm -ri cats
            ```

- ### Summary of commands ###
    - ls, which **l**i**s**ts the contents of a directory.
    - cd, which **c**hanges your working **d**irectory.
    - pwd, which **p**rints your **w**orking (current) **d**irectory.
    - open-xdg, which opens a file or a directory in the gui.
    - touch, which creates a new file with a specified extension or file type.
    - mkdir, which **m**a**k**es (creates) a new **dir**ectory.
    - rm, which permanently **r**e**m**oves a file.
    - rmdir, which permanently **r**e**m**oves an empty **dir**ectory.
    - rm -r, which permanently **r**e**m**oves a directory and its contents "recursively" (without confirmation).
    - rm -ri, which permanently **r**e**m**oves a directory and its contents "recursively" (with confirmation).
