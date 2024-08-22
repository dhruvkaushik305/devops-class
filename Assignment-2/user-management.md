# User/Group Management

Before doing anything with user/groups let us first see which user are we currently logged into. Use `whoami` to see the current user.
`id username` returns userid, groupid and groups that the user is associated with.

### User Id's
Let us understand these uid's first
1. uid 0 is reserved for the root.
2. uid 1-99 is reserved by the system and are statically assigned. This means that the system creates these users and will always have the same user id.
3. uid 100-999 is reserved for system administrators. These are dynamically allocated which means these would vary from system to system.
4. 1000+ refers to other users

### Group Id's
Similarly we have group id's or gid's
1. 0 is for the root
2. 1-99 is reserved by the system for predefined accounts
3. 100+ is for other groups

### Viewing the users and the groups
To see the user information we can simply cat the `passwd` file.
Running `cat /etc/passwd` we get a list of all the users associated with this system. The structure is `username:password:UID:GID:description:homedir:shell`.
In the earlier days that password hashes were stored here which were later removed and shifted to a different file which we will see in a minute. 
Here `homedir` represents the path to the home directory of the user and `shell` refers to the shell interpreter to be used when this user logs in. Note that not all users have a definite shell. Some users are made by the system for its functioning and are not intended to login to. These accounts thus have a `nologin` shell which basically terminates the connection if the someone tries to login because it is not inteded to.
To view the shells one can `cat /etc/shells`

The passwords are stored in the `/etc/shadow` which can only be accessed by the root. This is where the password hashes are stored. This includes the username, password hash, last changed, minimum number of days required between password changes, maximum number of days the password is valid, number of days before that the user is warned to change the passwod, number of days the password expires and the account in disabled and the date ofexpiration of the account.

Viewing the groups we have `cat /etc/group` which has all the group information. This inclues the group, gid and the accounts assiciated with this group. Yes groups also have their shadow file at `/etc/gshadow`

### Modifying the users
Now that we know the current state of our system, it is time to fiddle with it. First things first, adding users. There are 2 commands which are generally used. `useradd` is the low level command which offers more flexibility and is a minimal binary to add users. `adduser` on the other hand is a perl script written on top of `useradd` which is more verbose and interactive. Also sets the default home directory and bash as the shell.
We'll be using useradd over here. `useradd testuser` simply creates the user. However this does not has any home directory or root permissions say. These can be modified using options. useradd has the following options
-r makes the new user a root user
-u used to specify a given uid while creating the user.
-g used to specify a given gid while creating the user.
These id's should be unique or won't create the user.
-d creates the home directory in the specified location passed as the arguement.
-m create a a default home directory for the user
-p is used to specify the password for the user
-s specifies the path to the shell for this user
-c stands for adding description like the full name of the user
-G takes the list of groups you want t add this user to

In addition to this we also have a `/etc/default/useradd` which contains some default config for the useradd. This allows easy user creation by simply `useradd -D testuser`. This will pick up the values from the default config which you can set as per your requirement.

For explicitly setting the password for a user we use `passwd username`

Obviously we all make mistakes and there would be some attributes that we would want to change of a user. This can be done using the `usermod` command. This can change the comments, home directories, gid, password, shell, uid, etc using the same options as the `useradd` command.
Apart from changing the above options this also has a couple of extra options like
-L locks a user's password. This disables password based authentication. To fully block the account and prevent all forms of login, set the EXPIRE_DATE to 1 (the timestamp for Jan 1 1970). The expiry date can be modified using the -e option
-U This unlocks the account of the user and enables password based authentication. To fully unlock an account, set the EXPIRE_DATE to 99999 (sets the date to the latest 32 bit signed integer timestamp that is January 19 2038)
-a used in conjuction with -G as -aG to append a new group into existing groups instead of resetting the groups to the new set of groups passed.

For deleting the user we have `userdel username`. This however does not remove the home directory or the user files. Use the -r option remove all the user's home diretory and files. We also have the -f flag that forces the user deletion even if te user is still logged in or some other user is using the directory of that user to be deletd. Use this flag with caution.

### Creating and deleting groups
To create a new group use `groupadd testgroup`. Similarly to delete a group we use `groupdel testgroup`

