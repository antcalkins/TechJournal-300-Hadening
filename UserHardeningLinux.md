# User Account Creation And Use Hardening (Linux)

## Account Creation

Creating a user on *most* linux distributions is done with the `useradd` command.

`useradd $username`

On some distros the -k (shell) and -m (home directory) are needed but fedora automaticly sets the home diectory to **/home/$username** and the user's shell to **/bin/bash**

On a distro that does not automaticly set those variables you would need

`useradd $username -m -d /home/$username -k /bin/bash`

Accounts ceated via this method do not have a password set by default setting it using the `passwd` command. `passwd $username` sets hte passwod forr a given user account.

## Directory hardening

By default new account home folders have their perrmissions set to 755, wich are relatively lax.`chmod 700 /home/$username` can be used to set the perrmission level to 700, wich only allows acsess by the owner. 

## Pasword Expiry

By default on linux passwords are forever, however by modifying `/etc/login.defs` that can be changed.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-07-21-21-52-05-image.png)

To set a password expiry on a previously made user using `chage -m 14 --M 90 -W 7`.

 To lock out a user after the 90 day window you can modify `/etc/default/useradd`.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-07-21-22-07-08-image.png)

Setting `INACTIVE=0` sets accounts to not be able to log in afte their password expiry.

For existing accounts  running  `chage -I $username has this effect.



To automate the prrocess of creating a hardened account.

`username="PUT_USERNAME_HERE" ;useradd -m -d /home/$username -k /etc/skel $un; chmod 700 /home/$username; chage -m 14 -M 90 -W 7 -i $username; passwd $username `






