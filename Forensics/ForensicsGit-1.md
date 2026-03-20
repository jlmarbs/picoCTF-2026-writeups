## DESCRIPTION
Can you find the flag in this disk image? HINT: `How can you checkout the files of a previous commit?`

## MY PROCESS
Same thing what we did in `Forensics Git 0`, we will go and find the `.git` folder for us to proceed with the challenge.
<img width="606" height="421" alt="image" src="https://github.com/user-attachments/assets/0e0de045-f331-4816-8899-0cce7650e461" />

Reading the `COMMIT_EDITMSG` does not reveal the flag anymore and that is when we are going to use the hint `How can you checkout the files of a previous commit?`

Since we need to look at the PREVIOUS commit, we will now look into the `objects` folder. Why there? Previous commits aren't stored in a special history file. They are objects, sitting in objects/ just like blobs and trees. The "history" is just each commit object pointing to its parent via SHA1 hash.
<img width="624" height="211" alt="image" src="https://github.com/user-attachments/assets/3d368e5d-9aac-4244-a7e4-04761084aaed" />

As we can see, we have 5 different objects. Now taking note on the hint which said about PREVIOUS commit, we will pick an object for us to extract.

But before picking any object to extract, we first need to identify the current commit hash. We do this by reading the master ref, which gives us the current commit hash:
<img width="612" height="454" alt="image" src="https://github.com/user-attachments/assets/bc4442a8-3fcb-4a8d-90a9-58f93266c3d6" />

This tells us that the 5f folder is the current (latest) commit. Decompressing it reveals a parent field, which points to the previous commit.
<img width="732" height="290" alt="image" src="https://github.com/user-attachments/assets/a9f133be-fefc-40c7-afa1-5739662eb20b" />

And since the commit message says removed flag, we will trace the parent hash which is`17` in the object folder.
<img width="753" height="372" alt="image" src="https://github.com/user-attachments/assets/fbc30a0f-344a-4f0c-92c6-3f6deb01002a" />

As we can notice, this is the first commit. There is no parent field, meaning this is where the chain starts. The commit message says Add flag, confirming the flag was added here. We will now follow the tree hash which points to a6 in the objects folder.
<img width="696" height="286" alt="image" src="https://github.com/user-attachments/assets/990ff44f-d477-482d-98cd-c4d9afb65d5c" />

The text file has been found but there is a garbled value after the flag.txt. We will now try to find out what that is in order to proceed.
<img width="789" height="129" alt="image" src="https://github.com/user-attachments/assets/b82db3c1-f109-4eb2-867d-32c0ac2cf34f" />

We can see the bytes f150f47a... which matches exactly the f1 object in our objects folder. Since tree objects only point to blobs for files, we now know f1 contains the contents of flag.txt.

Decompressing the f1 object reveals the following:
<img width="781" height="304" alt="image" src="https://github.com/user-attachments/assets/48d1331c-94a6-4e22-92fc-0c98812fa5c1" />

That's the flag!

FLAG: `picoCTF{g17_r3m3mb3r5_d4ddf904} `
