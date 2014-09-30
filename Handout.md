git clone https://github.com/tracykteal/shell-ecology.git -b gh-pages

    cd shell-ecology

`cd` stands for 'change directory'

    ls

`ls` stands for 'list' and it lists the contents of a directory.
Let's go look in the 'data' directory.

    cd data
    ls
    ls -F

Anything with a "/" after it is a directory.  
Things with a "*" after them are programs.  
It there's nothing there it's a file.

You can access the manual using the `man` program.

    man ls

Space key goes forward  
Or use the arrow keys to scroll up and down.  
When you are done reading, just hit `q` to quit.

    pwd

This stands for 'print working directory'. The directory you're currently
working in.

Examining contents of directories
Type:

    cd

Then enter the command:

    ls shell-ecology

This will list the contents of the `shell-ecology` directory without
you having to navigate there.

    cd
    cd shell-ecology/data/hidden

and you will jump directly to `hidden` without having to go through
the intermediate directory.

Tab completion is awesome.

Full path

    cd /home/username/shell-ecology/data/hidden

Relative path

    cd shell-ecology/data/hidden

In the shell the tilde character, ~, is a shortcut
for your home directory.

    ls ~

The shortcut `..` always refers to the directory
above your current directory.

    ls ..

prints the contents of the directory one up from
where you are.

The `*` character is a shortcut for "everything". Thus, if
you enter `ls *`, you will see all of the contents of a given
directory.

    ls *csv

You can also review your recent commands with the `history` command.  

    history

to see a numbered list of recent commands

If your history looked like this:

    259  ls *
    260  ls /usr/bin/*.sh
    261  ls *R1*fastq

then you could repeat command #260 by simply entering:

    !260

(that's an exclamation mark).

The easiest way to examine a file is to print out all of the
contents using the program `cat`. Enter the following command:

    cat surveys.csv

This prints out the contents of the `surveys.csv` file.

The program, `less`, is useful when files are big and
you want to be able to scroll through them.

    less surveys.csv

`less` opens the file, and lets you navigate through it. The commands
are identical to the `man` program.

The commands `head` and `tail` let you look at
the beginning and end of a file respectively.

    head surveys.csv
    tail survyes.csv

The `-n` option to either of these commands can be used to print the
first or last `n` lines of a file. To print the first/last line of the
file use:

    head -n 1 surveys.csv
    tail -n 1 surveys.csv

We can search within files without even opening them,
using `grep`. Grep is a command-line utility for searching
plain-text data sets for lines matching a string or
regular expression.

Search for that sequence 5404 in the surveys.csv file

    grep 5404 surveys.csv

We get back the whole line that had '5404' in it. What if we wanted not
just that line but the 3 entries after it as well.

    grep -A 3 5404 surveys.csv

The `-A` flag stands for "after match" so it's returning the line that
matches plus the three after it. The `-B` flag returns that number of lines
before the match.

The redirection command for putting something in a file is `>`

Let's try it out and put all the entries that contain 'RM'
in the survys.csv in to another file called 'good-data.txt'

    grep "RM" surveys.csv > good-data.txt

The prompt should sit there a little bit, and then it should look like nothing
happened. But type `ls`. You should have a new file called good-data.txt. Take
a look at it and see if it has what you think it should.

Note: The '>' command will write over any file that's already there without asking.  
>> will append to the end of an existing file.

The pipe command '|' takes the output of the first
thing and then puts it in to the second part

    grep "RM" surveys.csv | less

The copy command 'cp' let's you copy files

    cp surveys.csv surveys_raw.csv

The `mkdir` command is used to make a directory. Just enter `mkdir`
followed by a space, then the directory name.

    mkdir raw

We can move files around using the command `mv`. Enter this command:

    mv surveys_raw.csv raw/

    rm raw/surveys_raw.csv

The `rm` file removes the file. Be careful with this command. It doesn't
just nicely put the files in the Trash. They're really gone.

The program 'nano' can be used to write files

    nano awesome.sh

To save the file and exit. At the bottom of nano, you see the "^X Exit". That
means that we use Ctrl-X to exit. Type `Ctrl-X`. It will ask if you want to save it. Type `y` for yes.
Then it asks if you want that file name. Hit 'Enter'.

Running programs

    cd shell-ecology/data
    hello.sh

This won't work because the shell isn't looking
in the right place for it.

    ./hello.sh

This will work, becuase we told it to look in this
directory '.' for the program.

The program can also be run by using the full path

    /home/username/shell-ecology/data/hello.sh

Or by entering:

    ~/shell-ecology/data/hello.sh

To run a program, you have to set the right permissions, make it
executable rather than just a text file.

    chmod +x awesome.sh

Now we can run the program

    ./awesome.sh

Congratulations, you just created your first shell script! You're set to rule the world.

