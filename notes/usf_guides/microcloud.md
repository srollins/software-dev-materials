Running Your Server on the Microcloud
=====================================


# Remote login

First, make sure you are comfortable with logging in to our CS systems using command line tools. 

1. The [tutoring center website](http://tutoringcenter.cs.usfca.edu/resources/logging-in-remotely.html) has instructions for logging in remotely.
2. Once you log in to `stargate` you will be able to access any of the machines inside of the CS firewall.
3. To log in to a microcloud node, simply ssh in the node, for example `ssh srollins@mc01.cs.usfca.edu`.
4. The microcloud nodes mount your `/home/username` CS directory.


# Jaring your code

You will next need to get your executable code to your home directory. One approach is to use `git` to clone your repository to your CS home directory, then compile your code there. Another approach is to package your code into a jar file.

You may package your code from the command line. I will provide instructions for packaging your code into an executable jar file through Eclipse.

1. Right-click on the project and select `Export`.
2. Choose `Java > Runnable JAR file` and select `Next`.
3. Select `Extract required libraries into generated JAR`.
4. Under `Launch configuration:`, select the class containing the main method that will run your server.
5. Select an appropriate `Export destination:` and click `Finish`.

# Using scp

Transfer your files to your home directory. One approach is to use scp. See [transferring files] (http://tutoringcenter.cs.usfca.edu/resources/transferring-files.html) for more detail.

Here is an example of how I would use scp from the command line to copy `example.jar` from my local system to my home directory and save it in a file named `example.jar` in a directory named `/cs514`:

`scp example.jar srollins@stargate.cs.usfca.edu:cs514/example.jar`

# SSH to the microcloud and run the program

Now that the JAR and input files are available from the microcloud node, you will need to SSH to your microcloud node. The microcloud nodes are behind the CS firewall. 

It is recommended that you watch the videos on SSH available on the CS support page: [Using SSH](http://www.cs.usfca.edu/support.html#login).

In my case, I used the following two commands to log in to my assigned node - mc01:

```
ssh srollins@stargate.cs.usfca.edu
ssh mc01.cs.usfca.edu
```

From any microcloud node, you will be able to access your home directory, so you can `cd` into the appropriate subdirectory, for example `cs514/SongFinder`.

Once you are in the correct directory, use [nohup](https://en.wikipedia.org/wiki/Nohup) to execute your program. This will ensure that your program continues to run even if you log out of the microcloud node. The command I used to do this was as follows:

``` 
nohup java -jar songfinder.jar &
```

### Exiting the program

`nohup` allows your program to continue running even if you log out, and `&` says to run your program in the background. 

Unfortunatelly, this makes it a bit difficult to exit your program. If you ran your program with the command `java -jar songfinder.jar` then you could easily use CTRL-C to exit the program. Not so with `nohup` and `&`.

If you make changes, redeploy, and try to run your program again you will find that you will get an error that the port is already in use. Only one program may listen on a given port at a time.

To find and kill a previous run of your program, use the following commands:

```
ps aux | grep java
```

This command lists all processes running and *pipes* the output of that into the `grep` command that will search for the keyword *java*. This will show you something like the following:

```
srollins 13983  0.1  0.6 7768088 104132 ?      Sl   12:37   0:02 java -jar songfinder.jar
```

This gives you the *process ID*, which you can use to kill the process as follows:

```
kill -9 13983
```

## SSH Tunnel

Because the microcloud is behind the CS firewall, you will not be able to directly access your server unless you are connected to the CSLabs network from Harney.

If you wish to test your program while connected to USF Wireless or another network, you will need to set up an SSH tunnel.

Google has several links to resources that will help you [set up an ssh tunnel using putty on windows](https://www.google.com/search?q=putty+ssh+tunnel&oq=putty+ssh+tunnel&aqs=chrome..69i57j0l5.4199j0j7&sourceid=chrome&es_sm=91&ie=UTF-8).

On the Mac, you can use a command similar to the following:

```
ssh -L 9000:mc01.cs.usfca.edu:8080 srollins@stargate.cs.usfca.edu
```

This command specifies that you want to forward traffic going to port 9000 on the local machine to mc01 port 8080 via the *gateway* stargate.

You will need to replace `mc01.cs.usfca.edu:8080` with your assigned microcloud node and port. You will also replace `srollins` with your username.

Finally, the `9000` is the port you wish to use locally. This can be anything over 1024 as long as you are consistent with how it is used.

Specifically, the command above assumes that I have logged into mc01.cs.usfca.edu and launched my server to listen on port 8080. 

In the browser on my local machine (i.e., my laptop connected to any network), I will open a browser and load `http://localhost:9000/all`. The browser will send the traffic to port 9000 on my local host, and the tunnel redirects that traffic to mc01 port 8080 via stargate!

