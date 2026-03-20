## DESCRIPTION
Can you find the flag in this disk image?

## MY PROCESS
For this challenge, we are given a disk image file.

For this one, we are going to check if there are partitions in the disk image by using `mmls` and this was the result:
<img width="873" height="290" alt="image" src="https://github.com/user-attachments/assets/246abf44-999e-4ed7-a68f-4e5f2ce9364a" />

Since there are 4 partitions, we are going to check what partition has a `home` directory.

Partition 0 is unallocated so we are going to go to Partition 2, and it does not have a home directory:
<img width="867" height="538" alt="image" src="https://github.com/user-attachments/assets/fade4a84-e640-4ebe-92be-89d5108f2a43" />

Partition 3 did not let `fls` determine the file system type so going to Partition 4 and this was the result:
<img width="546" height="355" alt="image" src="https://github.com/user-attachments/assets/c8697fee-3fe9-4e93-8ce5-caf1a90a0f1e" />

We found the `home` directory! Moving on with the challenge since the title says about Forensics GIT, we are going to focus on finding the `.git` folder.

Moving through each directory, we will still also use `fls -o 1140736 disk.img` and we will just specify the offset of the directory we want to go in after the file:

<img width="614" height="467" alt="image" src="https://github.com/user-attachments/assets/75521077-aa47-428d-8494-2691a3c1f1c1" />

While traversing through the directories, we have found the `.git` folder and a note.txt that might be a hint, so we will extract the note.txt with `icat`.
<img width="1096" height="186" alt="image" src="https://github.com/user-attachments/assets/d5919b3a-3b3c-4bc4-b444-b0abc6fafcef" />

After reading the text file, it only tells us to wrap the leetspeak phrase between the flag format, so we will go to the `.git` folder to find that specific phrase.
<img width="603" height="302" alt="image" src="https://github.com/user-attachments/assets/4ed1b51f-8939-434e-a163-1d1005746f54" />

When dealing with Git, we should always check places where a flag might be hidden. One of the first places to inspect is `COMMIT_EDITMSG`, since it stores the most recent commit message and may still contain hidden or overlooked data such as a flag.
<img width="629" height="87" alt="image" src="https://github.com/user-attachments/assets/8f110770-4109-4ac4-b739-6f007068b2c2" />

The phrase is found! Wrap the phrase around the flag format and you will solve the challenge.

FLAG: `picoCTF{g17_1n_7h3_d15k_041217d8}`
