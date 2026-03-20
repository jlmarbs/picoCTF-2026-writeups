## DESCRIPTION
The agents interrupted the perpetrator's disk deletion routine. Can you recover this git repo? HINT: `We think the deletion was interrupted before any git objects were touched`

## MY PROCESS
Same thing what we did in Forensics Git 0 and 1, we will go and find the .git folder for us to proceed with the challenge.
<img width="1097" height="348" alt="image" src="https://github.com/user-attachments/assets/1f3be83b-6a4c-4a3b-8106-17521fa30f8c" />

This time, since the challenge specifically said about recovering the repository, we will check the `logs` folder first to check all logs.
<img width="1106" height="344" alt="image" src="https://github.com/user-attachments/assets/3194ae65-7d0b-4d98-bd18-5ad7c9987528" />

As we can see, there is a specific commit wherein the secret hideout log was removed. Now our task is to check what's on that specific commit that was removed.

The first thing we need to do is to retrieve the git repo so that we can do git commands by mounting the disk image and copy the whole repository:
<img width="1104" height="222" alt="image" src="https://github.com/user-attachments/assets/75fa83d4-5beb-4b5b-b720-abd317c79549" />

<img width="1106" height="204" alt="image" src="https://github.com/user-attachments/assets/67059269-86d8-4c87-bc8f-a2fc3fba7caa" />

We can now perform git commands on the repository!

<img width="500" height="179" alt="image" src="https://github.com/user-attachments/assets/5f5ca8e2-12a0-41f4-b46c-c15aed930a10" />

The next thing we need to do is to get the specific commit which is `e80b38b3322a5ba32ac07076ef5eeb4a59449875` to check what was inside of the secret hideout log before it was removed.

<img width="832" height="408" alt="image" src="https://github.com/user-attachments/assets/e191e828-851e-4dc8-a69d-7f806bbea15e" />

The flag is found!

FLAG: `picoCTF{g17_r35cu3_16ac6bf3}`
