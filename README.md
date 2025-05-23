# linuxAndWindowsPersianFonts
The standard type of Persian and English fonts

Linux standard Persian and English fonts for using LibreOffice and any other Apps

If you want fonts just for yourself not system wide use this directory>>>    ~/.local/share/fonts

Many fonts are packaged for Ubuntu and available via the "Fonts" category of the Ubuntu Software Center. If you prefer apt-get, search for packages starting with otf- or ttf-.

Font files that are placed in the hidden .fonts directory of your home folder will automatically be available (but /etc/fonts/fonts.conf indicates it will be removed soon.). You can also place them in the ~/.local/share/fonts directory on newer versions of Ubuntu per the comments below.

You can also double-click on the font file (or select Open with Font Viewer in the right-click menu). Then click the Install Font button.

Important: for system wide use, you can use /usr/local/share/fonts/myfonts and /usr/share/fonts/myfonts. the myfonts directory is optional and it's better to put fonts from different sources to different directories and name them like the source name was so if there was any problem you can troubleshoot it simpler. Then reboot (or manually rebuild the font cache with fc-cache -f -v).

Warning: If you use apps like LibreOffice or any thing from snap store or flatpak then they might not know the system wide fonts. in this case you can use ~/.local/share/fonts/ too, to ensure this kind of apps will work with your fonts fine.

Warning: all the fonts extensions  should use lower case characters like font.ttf and the name of the fonts should not have space in between, you can use "-" or "_" instead of space or push the names of one font together like my-font.ttf or myfont.ttf not "my font.ttf".
if you have this problem use the following script to change the name of all the font files and replace space with "-".

go to the fonts directory and open the terminal in that directory and paste the following script for removing the space between the font names.

for f in *\ *; do
  mv "$f" "${f// /-}"
done

for turning the fonts uppercase characters extensions like font.TTF to lower case like font.ttf use the following command. this command is useful for any file extension not just TTF to ttf for example Report.PDF to Report.pdf

for f in *.*; do mv -- "$f" "$(dirname "$f")/$(basename "$f" | sed 's/\(.*\)\.\(.*\)/\1.\L\2/')" ; done

Then restart the system or use this command "fc-cache -f -v" to refresh the fonts caches But restarting the system might be better for all apps to know the new fonts.

Warning: the font directory permissions should be like the bellow lines
permissions for system wide: sudo chown -R root:root for both directories "/usr/share/fonts/" and  "/usr/local/share/fonts"
permissions for user use: DO NOT USE SUDO OR SUDO -R FOR THIS COMMAND JUST EXECUTE IT IN YOUR PERSONAL NORMAL USER MODE SHELL.
chown -R $USER:$USER ~/.local/share/fonts/

IMPORTANT AND HELPFUL: Very helpful command if you have many fonts in subfolders inside one folder!!!
Here's a simple bash script that will recursively find all .ttf files inside your current directory (and its subdirectories) and move them into a new folder called myfonts:

go to the main folder and open the terminal and paste the following commands

# Create the destination folder if it doesn't exist
mkdir  myfonts

# Finds all .ttf files and move them to myfonts folder
find . -type f -name "*.ttf" -exec mv -v {} myfonts/ \;


 [Amir Vahidi](https://github.com/amirvahidi-ir).

Peace 
