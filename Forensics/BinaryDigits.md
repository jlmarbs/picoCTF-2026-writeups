## DESCRIPTION
This file doesn't look like much... just a bunch of 1s and 0s. But maybe it's not just random noise. Can you recover anything meaningful from this?

## MY PROCESS
For this challenge, we are given a `.bin` file and when trying to read it, it only displays 0s and 1s.
<img width="1093" height="505" alt="image" src="https://github.com/user-attachments/assets/df166e82-2aa1-401a-a1dc-e39520e6c594" />

Noticing the binary, we will decode the binary thru `CyberChef`.

Decoding the binary with `From Binary` results to this:
<img width="1092" height="359" alt="image" src="https://github.com/user-attachments/assets/6ebf929a-9f6d-44ce-9c31-2c7c6eae73f4" />

As we can see, there is an identifiable file header `JFIF`, now we will try to render the image to see if the flag is there.

After using `Render Image` recipe, this was the result:
<img width="1092" height="350" alt="image" src="https://github.com/user-attachments/assets/e52170c5-3639-458e-a9d0-f0b3b862a6b4" />

Flag found :)
FLAG: `picoCTF{h1dd3n_1n_th3_b1n4ry_2f96e9a1}`
