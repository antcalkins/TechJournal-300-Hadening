# Windows Hardening Part 1

## Local Security Policy

Open Local security Policy.

<img src="file:///home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-08-10-20-53-49-image.png" title="" alt="" width="430">

In this menu there hundreds of options that can be set depending on your needs.

### Account and Password Policy

One of the most important things for good security is complex passwords, by enforcing complexity and length policy you can increse security, a good length is 12 chars, many more and they may be easily forgotton or mistyped.

Anoter essential Control is setting lockouts, this prevents brute force attacks by timing out that user's ability after a given number of failed attempts.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-08-10-20-59-25-image.png)

### Auditing

The pther pillar of security is visibility the settings in Audit policy will give your security team/you insights into activity on the system to be able to pick out anomolous behavior.

## Windows Defender / Security settings

To prevent untrusted applications from modifying sensitive folders or files, Enabling Controled Folder acsess will help mitigate some malisious file modifications. NOTE: still back up data that you care about protecting, no security control is perfect.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-08-10-21-05-46-image.png)

Enabling a firewall is a simple but effectiv esecurity measure, if an attacker were to attempt to connect if they were on the same network.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-08-10-21-07-59-image.png)

# Windows Hardening Part 2

## Local Security Policy

By Enabling AppLocker we cann limit which applications uisers can run on a system.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-08-10-23-13-53-image.png)

From this screen in Local Security Policy go to configure enforcement and set the settings that you want ,audit is less of a headache and will log all policy violations, enforced will block the app from running if it violates, so it can break things.

In an elevated command prompt enter `sc config appidsvc start=auto` to start the AppLocker service on startup. then set policies.

![](/home/acalkins/.var/app/com.github.marktext.marktext/config/marktext/images/2021-08-10-23-18-39-image.png)

Since we are mainly focused on applications right click in the right pane and click create default. that will enable system applications and those in ProgramFiles to execute, anything else needs to be added. The rule below will allow a user to run an executable from the "Apps" directory in their home.


