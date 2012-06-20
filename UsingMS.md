The Metasploit Framework (MSF) is a dynamic, extensible penetration testing platform, offering an array of tools and exploits for testing against target systems.  These tools offer capabilities ranging from custom exploit preparation to exploit deployment.  But Metasploit isn't just a collection of tools and exploits, it's a full operational environment and foundation that one can greatly expand.  (It also comes in several editions: Community, Express and Pro.)

Quick note: you'll have a lot more fun if you set up a test environment (including target machines / services) for testing Metasploit; see this page for more information 
  * http://www.metasploit.com/learn-more/how-do-i-use-it/test-lab.jsp

Let's get started...

Knowing the available Framework interfaces is key to understanding the variety of tools available to you and honing a strategy to use these.  For the sake of keeping it initially simple, we'll focus on some of the core interfaces: msfconsole, msfcli, msfweb, msfgui, msfencode...Metasploit consists of much more than these (more on that later).  Note that all following examples are demonstrated on a Linux platform, and we're assuming you've already installed the Framework.

Sagely wisdom: Strategy without tactics is the slowest route to victory. Tactics without strategy is the noise before defeat. -Sun Tzu

--------------------
Let's start with msfconsole...msf >
--------------------

[[[MSFCONSOLE SCREENSHOT]]]

MSFconsole is a powerful, interactive command line environment to interface with the Framework.  It provides the widest and speediest access to many of the Framework's capabilities, so it's a great interface to learn.  To launch MSFconsole, simply open a command line window and enter 'msfconsole'.  You'll see the image above.  From the "msf >" prompt, you can enter 'help' or '?' at any time to get assistance (see "Core Commands" list further below for an overview of these.)

Head to your "msf" prompt and type "show".  You'll see a long list of available modules broken out by categories: Encoders, NOP (No OPeration) Generators, Exploits, Payloads, Auxiliary, and Post.  Take some time and look through this list and get familiar with what's available, as this will help you utilize msfconsole to its full extent.





msf > help
Core Commands
=============

    Command       Description
    -------       -----------
    ?             Help menu
    back          Move back from the current context
    banner        Display an awesome metasploit banner
    cd            Change the current working directory
    color         Toggle color
    connect       Communicate with a host
    exit          Exit the console
    help          Help menu
    info          Displays information about one or more module
    irb           Drop into irb scripting mode
    jobs          Displays and manages jobs
    kill          Kill a job
    load          Load a framework plugin
    loadpath      Searches for and loads modules from a path
    makerc        Save commands entered since start to a file
    popm          Pops the latest module off of the module stack and makes it active
    previous      Sets the previously loaded module as the current module
    pushm         Pushes the active or list of modules onto the module stack
    quit          Exit the console
    reload_all    Reloads all modules from all defined module paths
    resource      Run the commands stored in a file
    route         Route traffic through a session
    save          Saves the active datastores
    search        Searches module names and descriptions
    sessions      Dump session listings and display information about sessions
    set           Sets a variable to a value
    setg          Sets a global variable to a value
    show          Displays modules of a given type, or all modules
    sleep         Do nothing for the specified number of seconds
    spool         Write console output into a file as well the screen
    threads       View and manipulate background threads
    unload        Unload a framework plugin
    unset         Unsets one or more variables
    unsetg        Unsets one or more global variables
    use           Selects a module by name
    version       Show the framework and console library version numbers
NOTE: To update msf, enter "svn update" at the msf prompt.



OLD CONTENT:
------------------------------------------------------------
------------------------------------------------------------
Start here:

* http://www.offensive-security.com/metasploit-unleashed/Main_Page
* https://dev.metasploit.com/redmine/projects/framework/wiki
* https://community.rapid7.com/community/metasploit/
* [[Evading Anti-Virus]]


Short Command Line Cheatsheet:
* msfupdate - updates the Framework


MSF Directory:
* docs
* encoders
* exploits
* extras
* lib
* msfcli
* msfconsole
* msfdldebug
* msfelfscan
* msfencode
* msflogdump
* msfpayload
* msfpescan
* msfupdate
* msfweb
* nops
* payloads
* sdk
* src
* t
* tools



Database troubleshooting
------------------------
If the database is not connecting automatically, first make sure it is running:
* Linux:`$ netstat -lnt | grep 7337` where 7337 is whatever port you told it to listen on during installation
* Windows: look for a postgres.exe process in task manager.

If postgres is not running, try starting it manually:
* Linux:`$ sudo /etc/init.d/metasploit start` or if you didn't choose to install as a service: `$ sudo /opt/metasploit*/ctlscript.sh start`
* Windows: Start -> Metasploit -> Services -> Start Services

Once postgres is running and listening, go back to msfconsole:
````
msf > db_connect
````
