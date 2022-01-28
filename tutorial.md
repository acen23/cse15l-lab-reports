# TUTORIAL: How To Prepare Your Computer For Remotely Running CSE15L Assignments
### Brought to you by Andrew Cen

![simu](https://acen23.github.io/cse15l-lab-reports/simu.jpeg)

As a student starting CSE 15L, you may be overwhelmed by the amount of setting up needed to begin even your first assignment. Your computer must have the basic
requirements to perform the remote access functions that you'll be using often. Have no fear, as this process is much simpler than it seems.

## Installing VSCode
1. Go to the Visual Studio Code website to find the download link: [link](https://code.visualstudio.com/)
2. Download and install the VSCode version for your specific OS. Once you're finished, you should have VSCode opened to a window like this:
![ss1](https://acen23.github.io/cse15l-lab-reports/Week1Screenshot1.png)

## Remotely Connecting
1. If you are on Windows, go through these steps before attempting ssh below: [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)
2. Look up your remote server account for CSE 15L here: [link](https://sdacs.ucsd.edu/~icc/index.php) (NOTE: If this account has not been activated yet, you must set a password first!)
3. Once you have your account credentials, type this command into your terminal, replacing `cs15lwi22zz@ieng6.ucsd.edu` with your specific username: `$ ssh cs15lwi22zz@ieng6.ucsd.edu`
4. Type in your password, and the successful login to the server should like similar to this: ![ss2](https://acen23.github.io/cse15l-lab-reports/remotelyconnecting.png)
5. To log out of the server, do Ctrl+D or run the command `exit`.

## Trying Some Commands
1. Now that you've learned a bit of commands in shell, try these few out in your local directory:
>
- `cd ~`
- `cd`
- `ls -lat`
- `ls -a`
>
2. Now try those out after ssh'ing into the remote server, while also trying this additional command:
>
- `ls /home/linux/ieng6/cs15lwi22/cs15lwi22abc`
>

Your commands should return similar results to this: ![ss3.1](https://acen23.github.io/cse15l-lab-reports/commands1.png) ![ss3.2](https://acen23.github.io/cse15l-lab-reports/commands2.png)

## Moving Files With `scp`
1. Create a new program called `WhereAmI.java` locally.
2. Write its contents as follows:
>
`class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}`
>
3. Try running it using `javac` and `java` on your computer.
4. Now, let's use the `scp` command to copy it over to the server. Run this command: `scp WhereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/`
5. Use `ls` once logged in to check for the file. It should be under the same name.
6. Now, try running step 3 again, this time on the remote server. Your results should look like this: ![ss4](https://acen23.github.io/cse15l-lab-reports/Week1Screenshot2.png)

## Setting An SSH Key
1. SSH keys allow us to quickly switch between local and server access without much security hassle. Run this command in your local home directory to start setting up your keys: `ssh-keygen`
2. To answer the second prompt, type in `/Users/joe/.ssh/id_rsa` where `joe` is your home directory name.
3. Press enter for the third prompt to avoid having a password. Press it again to confirm.
4. If you're on Windows, follow these extra steps: [link](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)
5. To copy over the **public** key to your remote server, first log onto your server and run `mkdir .ssh`
6. Log out of the server and run `scp /Users/joe/.ssh/id_rsa.pub cs15lwi22@ieng6.ucsd.edu:~/.ssh/authorized_keys`. Don't forget to replace `joe` with your directory name.
7. Now that it's setup, you should run ssh again to see the difference. It should look like this: ![ss5.1](https://acen23.github.io/cse15l-lab-reports/key1.png) ![ss5.2](https://acen23.github.io/cse15l-lab-reports/key2.png)

## Optimizing Remote Running
1. There are a few techniques that can be used on the command line to optimize the efficiency of our steps going forward:
>
- You can add remote commands on the same line as ssh by adding quotation marks: `ssh cs15lwi22@ieng6.ucsd.edu "ls"` ![ss6.1](https://acen23.github.io/cse15l-lab-reports/optimize1.png)
- You can also combine multiple commands on the same line in general by separating them with semicolons: `cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI` ![ss6.2](https://acen23.github.io/cse15l-lab-reports/optimize2.png)
>
2. By combining the techniques, you can log into the remote server and complete quick commands all with just a few lines. For example, let's compare the regular procedure with the quickest procedure of making local changes to a java file, and then copying and running remotely:
- After making this local change below to the java file, the number of keystrokes to follow will be measured: ![ss6.3](https://acen23.github.io/cse15l-lab-reports/optimize2-1.png)
- The number of keystrokes for the following procedure was counted to be **125**: ![ss6.4](https://acen23.github.io/cse15l-lab-reports/optimize2-2.png)
- The number of keystrokes for the optimized procedure was counted to be **118** (note that it only took one line of code): ![ss6.5](https://acen23.github.io/cse15l-lab-reports/optimize2-3.png)
