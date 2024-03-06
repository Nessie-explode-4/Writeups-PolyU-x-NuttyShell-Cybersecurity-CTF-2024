# Detective Conan 名偵探柯南 (Misc) (466 points, 17 Solves)

### Challenge Description:
```
There is only one truth! But the truth is in the past...if only there is a way back...
真相永遠只有一個！但係真相只存在於過去...如果有部時光機就好喇...

Author 作者: PurpleSe4shell
```

A .eml file given to us, and when we open it, we can see the following message:
![image](https://github.com/Nessie-explode-4/Writeups-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/assets/68149951/bc7cdab8-83ef-4fd6-a3eb-67581699e9fe)


And a photo is also attached on the email:
![WhatsApp Image 2024-03-03 at 14 37 58_ad631025](https://github.com/Nessie-explode-4/Writeups-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/assets/68149951/4d6c0827-8b5b-4f14-8f16-123fd6bd6c43)



We have save the .jpg file and open the .jpg file with the hex editor, and we can saw lot of secret-directive.nuttyshell.cc on the file begining
> Photo wait to be added

We try to enter the secret-directive.nuttyshell.cc to our browser, and we found that there only have cat video and hint
"I'm hosted with GitHub Pages."
"Nothing to see here now execept cat videos.. if only there is a way back..."
![image](https://github.com/Nessie-explode-4/Writeups-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/assets/68149951/777c3162-f4bc-4730-8222-5c47ed55b490)

When taking about going back, we have think of wayback machine, so we have try to enter the link to the wayback machine
but only the same pages show up
![image](https://github.com/Nessie-explode-4/Writeups-PolyU-x-NuttyShell-Cybersecurity-CTF-2024/assets/68149951/cd4f4173-9a52-48ad-bee6-6e4e832ee467)


So we have decide to... 
> Continue with the thing you said in dc

Then we try to enter "purplese4shell.github.io" into the wayback machine
And the following pages appear, simply just the cat video but it also have serect link "Shhhhhh! This is a Secret!"
> Photo here

And we click on to the link and link to a google drive "https://drive.google.com/file/d/1F_EpcMEGODsijaKuo_4zrab48b6GzQJS/view?usp=drive_link"

When we open the google drive, we will see the .txt file and the flag is inside
> Photo here

Flag
> PUCTF24{B3_m1nDfuL_0f_ur_D1giTaL_F00tprint_i2ofma58b}
