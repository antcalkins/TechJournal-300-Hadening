# Windows Hardening Part 1

## Local Security Policy

Open Local security Policy.

![image](https://user-images.githubusercontent.com/70460747/128965139-3b71cdc1-d6c9-4a5b-abab-d6f6ebcb08b4.png)

In this menu there hundreds of options that can be set depending on your needs.

### Account and Password Policy

One of the most important things for good security is complex passwords, by enforcing complexity and length policy you can increse security, a good length is 12 chars, many more and they may be easily forgotton or mistyped.

Anoter essential Control is setting lockouts, this prevents brute force attacks by timing out that user's ability after a given number of failed attempts.

![image](https://user-images.githubusercontent.com/70460747/128965228-c280e3db-c298-4bf1-b34a-1bdcadda25f9.png)


### Auditing

The pther pillar of security is visibility the settings in Audit policy will give your security team/you insights into activity on the system to be able to pick out anomolous behavior.

## Windows Defender / Security settings

To prevent untrusted applications from modifying sensitive folders or files, Enabling Controled Folder acsess will help mitigate some malisious file modifications. NOTE: still back up data that you care about protecting, no security control is perfect.

![image](https://user-images.githubusercontent.com/70460747/128965255-bde24fed-9e29-4d95-b870-238f2d6cc9fd.png)

Enabling a firewall is a simple but effectiv esecurity measure, if an attacker were to attempt to connect if they were on the same network.

![image](https://user-images.githubusercontent.com/70460747/128965284-ac1351f9-8800-4643-a705-30a218a62b6f.png)

# Windows Hardening Part 2

## Local Security Policy

By Enabling AppLocker we cann limit which applications uisers can run on a system.

![image](https://user-images.githubusercontent.com/70460747/128965416-c37a8c7b-cc84-4216-99fd-0cd8ce217887.png)

From this screen in Local Security Policy go to configure enforcement and set the settings that you want ,audit is less of a headache and will log all policy violations, enforced will block the app from running if it violates, so it can break things.

In an elevated command prompt enter `sc config appidsvc start=auto` to start the AppLocker service on startup. then set policies.

![image](https://user-images.githubusercontent.com/70460747/128965453-858e1572-ba16-4276-81c6-eaec330a3c23.png)


Since we are mainly focused on applications right click in the right pane and click create default. that will enable system applications and those in ProgramFiles to execute, anything else needs to be added. The rule below will allow a user to run an executable from the "Apps" directory in their home.

![Uploading image.png…]()

