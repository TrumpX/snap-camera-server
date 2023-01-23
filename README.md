# SnapCameraPreservation

The purpose of this project is to allow users to still use and find snap chat lenses with the snap camera application after the Jan 25th, 2023 shutdown.

This project uses a modified version of the 1.21.0 version of Snap Chat for Windows. Be sure to install that one before following the instructions on this page.

# Instructions for PC
Head over to https://snapchatreverse.jaku.tv/snap/ and make sure you have 1.21.0 installed. Provide the site the 1.21.0 version of "Snap Camera.exe" located at the default install location of "C:\Program Files\Snap Inc\Snap Camera". Make sure the 1.21.0 PC patch file is selected on the site, and make sure you replace the original file with the newly created patch file, you will need to rename the patch file to make it match.

I cannot host the EXE due to possible copyrights but I can patch it if you provide the original exe.

You'll know you are communicating with my server because a new category will be listed in the app called "Jaku Snap Backup".

If you see the above, go ahead and click on each of your saved lenses and activat them once to ensure they are backed up. After that you are free to sit back and relax.

# Instructions for Mac
Patching the application similar to Windows does not work. The built-in security of MacOS is preventing modified binaries to run, and attempts to resign are failing. However another solution for MacOS users exists, it's not my favoriate approach, but it does work and is available for users.

Download the studio-app.snapchat.com.crt file in this repository. Double-clicking it should open up your Keychain Manager, click on the login option on the left-hand side of the Keychain Manager, and then on the right-hand side click Certificates. You should see studio-app.snapchat.com listed with a red icon to the left of the name. Go ahead and right-click on this file and select "Get Info", click the Trust arrow at the top and for the option "When using this certificate" select "Always Trust", close this window and it should prompt you for your MacOS password.

Almost done!

Open up terminal, you can type terminal into spotlight. Next you'll need to type this into the terminal ```echo "66.228.41.64    studio-app.snapchat.com" | sudo tee -a /etc/hosts```, it will prompt for your local computers password. But from there you should be all set.

With that you can now close the terminal window and open Snap Camera, if everything works you should see "Jaku Snap Backup" as one of the categories.


# How does this work?

I've modified the Snap Camera.exe (for Windows) to use my servers instead of the Snap Chat servers. This was done with a hex editor and 2 modifications were made. Instead of communicating with studio-app.snapchat.com it now communicates with snapchatreverse.jaku.tv.For Mac users we aren't changing the host but instead telling it that the hosts IP is something else and installing a self-signed certificate  By doing so my server then communicates to the Snap servers to get the lenses data as if you were accessing it directly and downloads the lenses to an S3 bucket on Amazon. 

I then wrote a server that relays the information from the camera app to the snap chat servers (for now), which downloads the lenses separately and communicates back to the app in the way it expects.  

# Where is the code?
Server code can be found in the server folder. After being sick for way to long I finally got around to clearning it up from the pervious attempts. You can see how the server works by relaying the information from the Snap Chat servers for now. I also created a reference folder which contains all the known endpoints and their expected responses.

# Who are you and why are you doing this?

I am Jaku. If you're familiar with the software on Twitch called Crowd Control then you're already familiar with some of my work as I run the company behind that. Or maybe you were an Animal Crossing fan and played in 2020 and used https://turnip.exchange, I along with another friend (Ross) built that. You can find more about me at https://about.me/jaku but overall I just like to build things and have been building things for Twitch streamers, gamers and others for over 7 years now. I have a background that allows for this sort of stuff, and I enjoy working on them. 


# I have more questions or comments.
Feel free to submit an issue on Github with questions or message me on Twitter at https://twitter.com/jaku. 
