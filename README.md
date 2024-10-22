
1. Extract password hash from the zip file:
zip2john file.zip › rame.hash
This command extracts the password hash from file.zip and saves it into a file called rame.hash.

2. Cracking the hash using John the Ripper.
john rame.hash
This command uses the John the Ripper tool to try and crack the password of the zip file by checking the hash saved in rame.hash.

3. Using a specific wordlist
If you have a wordlist file, you can specify it for John to use:
john rame.hash --wordlist-wordlistfile
This command tells John to check each password in wordlistfile against the rame.hash.

4. If the wordlist is too big and you only want the last or first part of it:
tail -n 50000 wordlistfile > new.txt
This command takes the last 50,000 lines of the wordlistfile and saves them to new.txt .
head -n 50000 wordlistfile > new.txt
This command takes the first 50,000 lines of the wordlistfile and saves them to new.txt.

5. Using the smaller wordlist:
john rame.hash --wordlist-new.txt
This command uses new.txt (the shortened wordlist) to crack the zip file password.

6. Using Crunch to generate a custom wordlist:
If you know the password is made up of numbers and has a length between 4 and 6 characters:
crunch 4 6 '123456789' > new.txt
This command creates a list of passwords that are 4 to 6 digits long, using the numbers 1-9, and saves it in new.txt.

7. If the username is provided (e.g., "patricia") and you are dealing with Linux password files:
sudo unshadow /etc/passwd /etc/shadow > nebismieri
This command combines the /etc/passwd and /etc/shadow files into one, called nebismieri, which is useful for cracking Linux user passwords.

8. Cracking a specific user's password:
john --format=crypt --user-patricia --incremental-digits nebismieri This command attempts to crack the password for the user patricia using only numeric values (digits).
