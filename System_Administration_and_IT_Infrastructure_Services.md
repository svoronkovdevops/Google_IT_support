
Introduction to System Administration and IT Infrastructure Services

## Content

[System Administration](#system-administration)

[IT Infrastructure Services](#it-infrastructure-services)

[Software and Platform Services](#software-and-platform-services)

[Directory Services](#directory-services)

[Data Recovery & Backups](#data-recovery--backups)

[Content](#content)

[Courses list](README.md#contents)



# System Administration

## What is System Administration?

**System administration** is the field in IT that's responsible for maintaining reliable computer systems in a multi-user environment.

System administrators -- or sysadmins -- have a diverse set of roles and responsibilities:
- Configuring servers;
- Monitoring the network;
- Provisioning/setting up new users in computers;
- And much more, handling many different things to keep an organization's IT infrastructure up and running.

**IT infrastructure** encompasses the software, the hardware, network, and services required for an organization to operate in an enterprise IT environment.


### Servers Revisited

A sysadmin is responsible for their company's IT services. These services include email, file storage, running a website, and are required so the company can be productive. And these services are all stored on servers.

A **server** is software or a machine that provides services to other software or machines.
- For example, a web server stores and serves content to clients through the Internet
- An email server provides email service to other machines
- An SSH server provides SSH services to other machines

Clients request the services from a server; and the servers respond with the services.

Server hardware can come in many different forms:
- They can be towers, similar to desktops
- Rack servers lay flat, are usually mounted in server racks, and provide multiple servers
- Blade servers are slim racks that stand upright, and provide even more storage space

#### KVM Switch
-KVM stands for "keyboard, video, & mouse"
- A KVM switch looks like a hub you can connect multiple computers to, and control them using one keyboard, mouse, and monitor.


### The Cloud

**Cloud computing** is the concept that you can access your data, use applications, store files, etc, from anywhere in the world; as long as you have an Internet connection.

"The cloud" isn't a magical thing--it's just a network of servers that store and process our data, via a data center.

A **data center** is a facility that stores hundreds or thousands of servers.

You could manage your own servers, or you could use data centers to manage your servers. Drawbacks of managed services include cost and dependency.

You might want to back up data on the cloud or a physical disk.


## Systems Administration Tasks

### Organizational Policies

In a small company, it's usually a sysadmin's responsibility to decide what computer policies to use.

A few common policy questions include whether users should be allowed to install software, require complex passwords, or view non-work related websites.


### User and Hardware Provisioning

Sysadmins have to be able to create new users and give them access to company resources; they also have to remove users from an IT infrastructure if users leave the company.

- Sysadmins are also responsible for user machines.
- They have to make sure a user is able to log in, and the computer has the necessary software that a user needs to be productive.
- Sysadmins also have to ensure that the hardware they are *provisioning* -- or setting up for users -- is standardized in some way.

Sysadmins also have to figure out the hardware lifecycle of a machine:
- When was it built?
- When was it first used?
- Did the organization buy it brand-new, or was it used?
- Who maintained it before?
- How. many users have used it in the current organization?
- What happens to this machine if someone needs a new one?

#### 4 Main Stages of Hardware Lifecycle
- **Procurement:** This is where hardware is purchased or reused for any employee;
- **Deployment:** This is where hardware is set up so that the employee can do their job;
- **Maintenance:** This is the stage where software is updated and hardware issues are fixed if and when they occur; 
- **Retirement:** This is the final stage, where hardware becomes unusable or no longer needed, and must be properly removed from the fleet.

An example of a typical hardware lifecycle:
- A new employee is hired by the company, and you're instructed to provision a computer;
- You allocate a computer you have from your inventory, or you order a new one;
- When you allocate hardware, you may need to tag the machine to keep track of which inventory belongs to the organization;
- Next you image the computer with the base image, preferably using a streamlined method;
- You name the computer with a standardized host name, to help with managing the machines;
- You install software the user needs on their machine;
- The new employee starts, and you streamline the setup process by providing instructions on how to use their new computer environment;
- Eventually, if a computer sees a hardware issue or failure, you investigate it;
  - If it's getting too old, you have to figure out where to recycle it and where to get new hardware;
- Finally, if a user leaves the company, you'll have to remove their access from IT resources and wipe the machine, so you can eventually reallocate it to someone else.

Imaging -- installing software and configuring settings on a new computer -- can get time-consuming. You'll have to learn automated ways to provision new machines so that you only spend minutes on this, and not hours.


### Routine Maintenance

When providing updates and maintenance for a fleet of machines, you don't want to immediately install updates as soon as they come in -- this would be way too time-consuming. 

Instead, to effectively update and manage hardware, you do what's called a **batch update**.
- A batch update is where, once every month or so, you update all your servers with the latest security patches.


### Vendors

Working with vendors or other businesses to buy hardware is commonly assigned to sysadmins.

Setting up business accounts with vendors like HP, Dell, Apple, etc is usually beneficial, since these companies can offer discounts to businesses.


### Troubleshooting and Managing Issues

Troubleshooting will take up most of your time as an IT support specialist.

Sysadmins have to troubleshoot issues at a larger scale.

Whatever the scenario, there are two critical skills for arriving at a good solution for your users:
1. Troubleshooting
  - Asking questions, isolating the problem, following the cookie crumbs, reading logs
2. Customer Service
  - Showing empathy, using the right tone of voice, dealing well with difficult situations


### In Case of Fire, Break Glass

To be prepared for anything, it's very important to make sure your company's data is routinely backed up somewhere. Preferably, far away from its current location.


## Applying Changes

### With Great Power Comes Great Responsibility

Avoid using administrator rights for tasks that don't require them.

Try to minimize the time spent in an administrative session.

Respect the privacy of others.
- Just because you can do something, doesn't mean you should do something.

Think before you type.
- Your actions can have much greater consequences as an administrator, compared to being a regular user.
- Writing out the steps you plan to take before doing them helps in two ways:
1. It allows you to plan ahead;
2. It serves as documentation.
- Documenting what you did is crucial when using administrator rights.
  - Recording the commands you executed lets you repeat the same process in the future and can fix problems that may arise later.

In Linux, the `script` command can record a group of commands as they are being issued along with their output.

In Windows PowerShell, there's an equivalent command called `Start-Transcript`

The recordMyDesktop tool can record the interaction with the graphical application.

With great power comes great responsibility
- The more you can do with your administrator rights, the more you can mess up.
- To minimize the impact of (inevitable) mistakes, make sure you can quickly revert your changes if something goes wrong.
- Make a copy of the state before changing it;
  - Keep your configuration in a version control system or by documenting what steps you need to go back to the previous state.

Reverting to the previous state is called a **rollback**.

Before you make a change, take a moment to think about what that would look like, and make sure you have copies of any information that could be lost.


### Never Test in Production

**Production** is the parts of the infrastructure where a certain service is executed and served to its users.

The **test environment** is usually a virtual machine running the same configuration as the production environment, but isn't actually serving any users of the service.

For an important service that must run during a configuration change, it's best to have a secondary or stand-by machine.

A **secondary** or **stand-by machine** will be exactly the same as a production machine, but won't receive any traffic from actual users until you enable it to do so.

For even bigger services, when you have lots of servers providing the service, you may want to have canaries.
- Canaries refer to a small group of servers to detect any potential issues in the larger changes you want to push out in the system.

Always use a test instance first, and only deploy the change to production after verifying that it works.


### Assessing Risk

The amount of time and effort to invest in changes depends on the risk involved.

We can assess the risk involved by considering how important the services to the infrastructure are, and how many users would be impacted if the service went down.

In general, the more users your service reaches, the more you'll want to ensure that changes aren't disruptive.

The more important your service is to your company's operations, the more you'll work to keep the service up.

You can also use these criteria to establish priorities for fixing a problem. If the problem is preventing people from doing their work, finding a solution to it should have a higher priority than solving a minor annoyance that can be worked around.


### Fixing Things the Right Way

- Before you start fixing a problem, make sure you can recreate the error, as you'll want to test your solution to make sure the problem is gone after you apply the fix.
- This is called a reproduction case.
  - A **reproduction case** is to create a roadmap to retrace the steps that led the user to an unexpected outcome.

When looking for a reproduction case, there are three questions you'll need to answer:
1. What steps did you take to get to this point?
2. What's the unexpected or bad result?
3. What's the expected result?

But remember: Always do this in your test instance, never in production.

Make sure you document all your steps and any findings.

After applying your fix, retrace the same steps that took you to the bad experience. If your fix worked, the expected experience should now take place.

[Content](#content)

--------------------------------------------------------------- IT Infrastructure Services-------------------------------------------------------------


## IT Infrastructure Services

### What are IT Infrastructure Services?

IT infrastructure services are what allow organizations to function. These include:
- Connecting to the Internet;
- Managing networks by setting up the network hardware;
- Connecting computers through an internal network;
- And many other tasks.


### Types of IT Infrastructure Services
You can buy or rent hardware for your servers and set them up on-site or somewhere else. 

#### Infrastructure as a Service

You can also use the cloud alternative to maintain your own infrastructure, which is called **Infrastructure as a Service (IaaS)**.
- IaaS providers give you preconfigured virtual machines you can use just as if you had a physical server
- Popular providers include:
  - Amazon Web Services and their Elastic Compute Cloud (EC2) instances
  - Linode
  - Windows Azure
  - Google Compute Engine

#### Networking as a Service (NaaS)

Networking can be integrated in an IaaS provider, but it's branched off in recent years into its own cloud service: **Networking as a Service (NaaS)**.
- NaaS allows companies to offshore their networking services, so they don't have to deal with expensive networking hardware
- Companies also won't have to set up their own network security, manage their own routing, set up a WAN and private Internets, etc.

#### Software as a Service (SaaS)

For software your company may require (word processors, spreadsheets, email clients, OS, etc), the cloud alternative to maintaining your own software is known as **Software as a Service (SaaS)**. These are services you can purchase that allow you to use them from a web browser.

#### Platform as a Service (PaaS)

If you want an all-in-one solution to building and deploying a web application, you can use something called **Platform as a Service (PaaS)**. 
- This includes an entire platform that allows you to build code, store information in a database, and serve your application from a single platform
- Popular options for PaaS are Heroku, Windows Azure, and Google App Engine

#### Managing Users, Access, & Authorization

A **directory service** centralizes your organization's users and computers in one location, so that you can add, update, and remove users and computers.
- Two of the most popular directory services are Windows Active Directory, and OpenLDAP
- Directory services can also be deployed in the cloud using **Directory as a Service (DaaS)**


## Physical Infrastructure Services

### Server Operating Systems

- For an organization, you'll typically want to install your services on a server operating system.
- A **server operating system** is a regularly operating system that is optimized for server functionality.
- These include functions like allowing more network connections, and more RAM capacity.
- Most operating systems have versions specifically made for servers:
  - Windows Server
  - Ubuntu Server
  - MacOS Server
- Server operating systems are usually more secure and come with additional services already built in.


### Virtualization

There are two ways you can run your servers:
1. Either on dedicated hardware;
2. Or on a virtualized instance on a server.

#### Performance
- A service running on dedicated hardware will have better performance than a service running in a virtualized environment
- This is because you only have one service using one machine, as opposed to many services using one machine.

#### Cost
- Server hardware can be expensive
- With virtualization, you can have ten services running on ten different virtual instances, all on one physical server
- It's cheaper to run several services on one machine than it is to run many services on multiple machines.

#### Maintenance
- Servers require hardware maintenance and routine operating system updates.
- Sometimes, you'll need to take the servers offline to do that maintenance.
- Virtualized service makes server maintenance much easier to do.
- With virtualized service, you can quickly stop the service, migrate it to another physical server, and take as much time as you need for maintenance.

#### Points of Failure
- Service on one physical machine can be trouble, if that machine has issues.
- You can easily move virtualized service off a machine and spin up the same service on a different machine as a backup.
- You can prevent a single point of failure on a physical machine if you have redundant servers set up (duplicate servers as a backup)


### Remote Access Revisited

- In Linux, the most popular remote access tool is OpenSSH
- To SSH into another machine:
  - You need to install an SSH client on the machine your connecting from;
    - `sudo apt-get install openssh-client`
  - And install an SSH server on the machine your'e connecting to.
    - `sudo apt-get install openssh-server`


## Network Services

### FTP, SFTP, and TFTP

File transfer services are a popular network use for organizations. A server dedicated to file transfer allows you to store huge directories and files; and transfer them from one computer to another using the Internet.

**File Transfer Protocol (FTP)** is a legacy way to transfer files from one computer to another over the Internet. It's still in use today.
- It's not the most secure way to transfer data, because it doesn't handle data encryption.
- It operates not too unlike an SSH service -- to access an FTP server, a computer has to install an FTP client
- FTP is still primarily used to share web content.

**Secure File Transfer Protocol (SFTP)** is a version of FTP that uses SSH and encrypts its files.

**Trivial File Transfer Protocol (TFTP)** is a simpler way to transfer files -- it doesn't require user authentication (which FTP does).
- A popular use of TFTP is to host installation files, booting computers through **preboot execution (PXE Boot)**


### NTP

One of the oldest Internet protocols in use today is the **network time protocol (NTP)**. It's used to keep the clock synchronized on machines connected to a network.

There are different ways to set up an NTP server:
- You can use a *local NTP server*, where you install NTP server software on your management server
  - Then, you install NTP clients on your machines, and tell those computers which NTP service to sync their time to.
- Or, you can use a *public NTP server*
  - These are managed by other organizations that your client machines connect to, in order to get synchronized time.
  - It's better etiquette to run your own NTP servers if you have a large fleet of machines.


### Network Support Services Revisited

#### Intranets
- An Intranet is an internal network inside a company
- It can house documentation, updates, and many other resources

#### Proxy Servers
- A proxy server acts as an intermediary between a company's network and the Internet.
- They receive traffic, and relay that traffic to the company network
  - This way, company network traffic is kept private from the Internet
- Proxy servers can also be used to monitor and log internal company network activity


### DNS

As a recap, **Domain Name System (DNS)** maps human-understandable names to IP addresses.

#### For Web Servers
If you own the domain name and host your web content yourself, it make sense for you to have the DNS servers that know that information.

#### For Internal Networks
- The other reason we might want our own DNS servers is so we can map our own internal computers to IP addresses
  - That way, we can reference a computer by name, instead of an IP address
- *Local host* is a common way to access a local web server.
- A DNS query first checks the local host file, then it checks the local DNS servers
  - But manually configured every single computer's local host files is not efficient
- Instead, you can set up a local DNS server that contains all the names mapped to their IP addresses
  - Then, you change the local network settings for all computers to use the DNS sever instead of the one given by the local ISP.
- Another option is to integrate your internal network with a directory service which handles user and machine info in its central location, like Active Directory
  - Once you set up DNS in your directory service, it will automatically populate with machine-to-IP address mappings (not manually)


### DHCP

- Recall that through DHCP, your computers will be "leased" an IP address from a DHCP server.
  - They automatically get IP addresses, you needn't manually set anything, and it makes expanding your IP address range an easy task (handled automatically)
- If you want to integrate DHCP with DNS, you need the address of your local DNS servers, what gateway you should assign, and the subnet mask that gets used.
- Then you have to configure the DHCP server software with this new information.
- By syncing the DNS and DHCP servers, whenever DHCP leases out new addresses, DNS updates IP address mappings automatically.



## Troubleshooting Network Services

### Unable to Resolve a Hostname or Domain Name

There are some situations where DNS can be tricky to navigate, since there can be many contributing factors. But as with any troubleshooting scenario, remember to keep isolating the problem down until you can get to a root cause.


## Managing System Services

### What Do Services Look Like in Action?

- Services such as DNS, DHCP, NTP, and others are **background processes**
  - Also known as **daemons** or **services**.
- This means the program doesn't need to interact with the user through the GUI or CLI to provide the necessary service.
  - The operating system ensures that the program is running.
- Each service has one or more **configuration files**, that you as a sysadmin will use to determine how you want the service to behave.
  - Services are usually configured to start when the machine boots, so that if there's a power outage or a similar event that causes the machine to reboot, you won't need a system administrator to manually start the service.


### Managing Services in Linux

You can check if there's an NTP daemon running on a Linux machine using the service command `service ntp status`

### Managing Services in Windows

In Windows PowerShell, `Stop-Service`, `Start-Service`, and `Get-Service` can be used to manage daemons.

You can list all services that are registered in the system using the `Get-Service` command; or through using the GUI's Services management console.


### Configuring Services in Linux

- Most services are enabled as soon as you install them. These are programs that are shipped with the defaults, that are good enough to safely start serving right away
- But not all services can provide default values that are suitable -- you will need to edit the configuration files before the service can go live.
- In Linux, the configuration files for the installed services are located in the `/etc` directory.

**lftp** is an FTP client program that allows us to connect to an FTP server.

**Reload** means the service re-reads the configuration without having to stop and start. This way, ongoing connections aren't interrupted, but new connections will use a new configutation.


### Configuring Services in Windows

As an example, you can access Windows's Internet Information Services (the feature offered by Windows to serve web pages) through Start > Control Panel > Turn Windows features on and off

You can configure through the GUI from here. (In this example, to install a web server services feature.)


[Content](#content)

-------------------------------------------------------------------------------------Software and Platform Services--------------------------------------------------------------------------------------

# Software and Platform Services

## Software Services

**Software services** are the services that employees use that allow them to do their daily job functions.

**Platform services** provide a platform for developers to code, build, and manage software applications.


### Configuring Communication Services

There are several methods of instant communication, in the business environment.

**Internet Relay Chat (IRC)** is a protocol that's used for chat messages. IRC operates in a client & server model, so lots of IRC client software can be used to connect to an IRC server.

Open IM Protocols

**Extensible Messaging and Presence Protocol (XMPP)** is an open-source protocol used in instant messaging applications and social networking services. Pidgin and Padium are two free applications that use XMPP.


### Configuring Email Services

To configure email services for the company, you need to have a domain name set up that you can use as the email domain (such as employee@ccompany.com).

There are two ways to set up email for a company
1. Run your own managed server
  - You set up the email service software on a server, then you create a DNS record for your mail server.
  - Remember that the **A record** is used for hostnames; but for email servers, we use **MX** for the **mail exchange record**.
2. Use an email service provider (like Google Suite)

#### Email protocols

**Post Office Protocol version 3 (POP3)** is an email protocol that downloads email from an email server onto your local device. It deletes the email from the email server, meaning you can only view the email from one device.
- Good for keeping your email storage under a certain quota
- Since your email can only be seen from your local device, POP3 has privacy benefits as well

**Internet Message Access Protocol (IMAP)** allows you to download emails from your email server onto multiple devices, and keeps your messages on the email server.
- This is one of the most popular ways to retrieve email

**Simple Mail Transfer Protocol (SMTP)** is a protocol used for sending email.
- Really the only email protocol for sending email, and that's SMTP.


### Configuring User Productivity Services

When considering software licenses, it's important to review the terms and agreements.


### Configuring Security Services

**Hyper Text Transfer Protocol Secure (HTTPS)** is the secure version of HTTP, which makes sure the communication your web browser has with the website is secured through encryption.

HTTPS is also referred to as "HTTP over TLS," or "HTTP over SSL." This is because there are two protocols that enable us to make our web servers secure.

The **Transport Layer Security (TLS)** protocol is the most popular way to keep communications secure over a network. TLS is widely used to keep web browsing secure; but it can be used in many other applications, too.

The second is **Secure Socket Layer (SSL)** protocol. SSL is a way of securing communication between a web server and a client. But, it's old and insecure, and has been deprecated in favor of TLS.
- TLS and SSL are often used interchangeably
- SSL version 3.0 was essentially TLS version 1.0
- But TLS is more secure and now superior

To enable TLS on a server so the site can use HTTPS, you need a digital certificate of trust from an entity called a *certificate authority*.
- The authority grants a certificate to your website saying it trusts that you control the web server
- It also verifies that you are who you say you are


## File Services

**File storage services** allow us to centrally store files and manage access between files and groups.

### Network File Storage

**Network File System (NFS)** is a protocol that enables files to be shared over a network.

NFS works with all operating systems; but there are issues with Windows. Samba is a better alternative for a Windows fleet (and is also compatible with other operating systems)

- SMB is the protocol that Samba implements, and is *not* the same as Samba
- When you create a Windows shared folder, it's created using the SMB protocol
- Samba itself is a software service suite used for file services

Other file storage service solutions include 

#### NAS
- **Network attached storage (NAS)** are computers that are optimized for file storage
- They usually come with an operating system that's been stripped down in order to just serve files over a network; and they come with a ton of storage space.


### Mobile Synchronization

When you synchronize data, you make sure that the data is the same in two or more places.


## Print Services

### Configuring Print Services

Along with managing print essentially, you'll also need to be able to deploy printer driver software so your users can print from their computers.

To set up a print server, all you have to do is install a print service on a server.

In Linux, a common print server that's usually pre-installed on machines is the **Common UNIX Printing System (CUPS)**

A cloud service provider is another way to manage printers.


## Platform Services

### Web Servers Revisited

A **web server** stores and *serves* content to clients through the Internet.

Among the many popular types of HTTP server software, the most widely used is the **Apache HTTP server** (or just **Apache**).

### What is a database server?

**Databases** allow us to store, query, filter, and manage large amounts of data.


## Troubleshooting Platform Services

### Is the website down?

**HTTP** status codes are codes or numbers that indicate some sort of error or info messages that occurred when trying to access a web resource.

- HTTP status codes that start with `4xx` indicate an issue on the *client-side*.
- The other common HTTP status codes you might see start with `5xx`
  - These errors indicate an issue on the *server-side*.
- HTTP status codes tell us more than just errors
  - Codes beginning with `2xx` tell us when our request is *successful*.


## Managing Cloud Resources

### Cloud Concepts

When you use **Software as a Service (SaaS)**, the software is already pre-configured and the user isn't deeply involved in the cloud configuration.

When you use **Infrastructure as a Service (IaaS)**, you're hosting your own services in the cloud. You need to decide how you want the infrastructure to look, depending on what you want to run on it. (Start small; then select more powerful instances as needed.)

When you set up cloud resources, you need to consider regions. A **region** is a geographical location containing a number of data centers.
- Each of these data centers is called a *zone*, and each zone is independent of the others.
- If one of them fails for some reason, the others are still available and services can be migrated without visibly affecting users.

You might also hear about different types of clouds:
- **Public cloud:** Cloud services provided to you by a third party
- **Private cloud:** When your company owns the services and the rest of your infrastructure -- whether on-site or in a remote data center
- **Hybrid cloud:** A mixture of both public and private clouds


### Typical Cloud Infrastructure Setups

- A **load balancer** ensures that each VM receives a balanced number of queries.
- **Autoscaling** allows the service to increase or reduce capacity as needed, while the service owner only pays for the cost of the machines that are in use at any given time.
- If you need data persistence, you have to create separate storage resources to hold that data and connect that storage to the VMs.
- Most cloud providers include *monitoring* and *alerting* solutions as part of their services.


### When and How to Choose Cloud

Most cloud providers offer free trials, so it's a good idea to test that out to see if they meet your needs, and to check how well your company's infrastructure integrates with the cloud provider's.


[Content](#content)



----------------------------------------------------------------------------Directory Services-------------------------------------------------------------------------------------------------------


# Directory Services

## Introduction to Directory Services

### What is a directory server?

A **directory server** contains a lookup service that provides mapping between network resources and their network addresses.

It's used to organize and look up organizational objects and entities, ranging from user accounts, user groups, telephone numbers, and network shares.

The ideal enterprise-quality directory server should support replication. **Replication** means that the stored directory data can be copied and distributed across a number of physically distributed servers, but still appear as one unified datastore for the querying and administering.

Replication is important because it provides redundancy, by having multiple servers available simultaneously. This means there will be minimal disruption to the service, in the event a server has a mishap.


## Centralized Management

### What is centralized management?

**Centralized management** is a central service that provides instructions to all of the different parts of an IT infrastructure.

Directory services provide centralized *authentication*, *authorization*, and *accounting*; also known as AAA.

**Role-based Access Control (RBAC)** is an easier way to manage access privileges at the group/classification level (not the individual level).

**Configuration management:** By centralizing the configuration management of your computers and software, you can create rules about how things should work in your organization.

Dedicated configuration management frameworks include *Chef*, *Puppet*, and *SCCM*.


## LDAP

### What is LDAP?

**Lightweight Directory Access Protocol (LDAP)** is used to access information in directory services over a network.

Two of the most popular directory services that use LDAP are **Active Directory** and **openLDAP**.

#### LDAP notation
- An LDAP *entry* is just a collection of information that's used to describe something.
- The format of an LDAP entry basically has a unique entry name, denoted by **dn** (or **distinguished name**)
  - Then attributes and values associated with that entry
  - **CN** is the common name of the object
  - **OU** is the organizational unit such as a group
  - **DC** is the domain component
- An example of an LDAP entry:
  - `dn: CN=name,OU=group,DC=address,DC=com


### What is LDAP Authentication?

With LDAP, there are different authentication levels that can be used to restrict access to certain directories.

In LDAP, the **Bind** operation authenticates clients to the directory server.

There are three common ways to authenticate:
- **Anonymous binding:** You aren't actually authenticating at all; depending on how it's configured, anyone could potentially access that directory.
- **Simple authentication:** You just need the directory entry name and password; this is usually sent in plain text, meaning it isn't secure at all.
- **Simple authentication and security layer (SASL):** This method can employ security protocols like TLS and Kerberos; SASL requires the client and directory server to authenticate using some method.
  - One of the most common methods is Kerberos, a network authentication protocol used to authenticate user identity, secure the transfer of user credentials, and more.


## Active Directory

### What is Active Directory?

**Active Directory (AD)** is the native directory service for Microsoft Windows.

- Active Directory can communicate via the LDAP protocol; and thus can interoperate with Linux, OSX, and other non-Windows hosts via the protocol.
- AD also becomes the central repository of *group policy objects (GPOs)*, which are ways to manage the configuration of Windows machines.

The **Active Directory Administrative Center (ADAC)** is a tool for performing tasks through AD.

Like with file systems, directory services are hierarchical.

- Everything you see in AD is an object.
  - Some objects are *containers*, which can contain other objects.
- Several of the default containers are just called "containers," and they serve as default locations for certain types of objects.
- Another type of container is called an *organizational unit (OU)*, which is like a folder or directory for organizing objects within a centralized management system.
- Ordinary containers can't contain other containers; but OUs can contain other OUs.

- In ADAC, a domain will have a short name (like "example"), and a DNS name (like "example.com")
- Objects -- particularly computers in the domain -- will be given a DNS name that lives in the domain's DNS zone.
  - A **forest** is the hierarchical level above a domain; a forest contains one or more domains.
  - AD accounts can share resources between domains in the same forest.
- Computer accounts are created when a computer is joined to the AD domain.

The service that hosts copies of the AD database are called **domain controllers (DCs)**. DCs provide several services on the network:
- Domain controllers get to decide when computers and users can log onto the domain.
  - They host a replica of the AD database and group policy objects;
  - They serve as DNS servers
  - They provide central authentication via Kerberos
  - They get to decide who has access to shared resources like filesystems and printers.

It's common for most domain controllers in the AD network to be the **read-write replicas**. This means that each have a complete copy of the AD database and can make changes to it; and these changes are then replicated to all other copies of the database on other DCs. 

Some changes to the AD database can only be made safely by one DC at a time; these changes are tasked to a single DC by granting it a **Flexible Single-Master Operations (FSMO)** role.

Joining a computer to Active Directory means two things:
1. AD knows about the computer and has provisioned a **computer account** for it;
2. The computer knows about the Active Directory domain and authenticates with it.


### Managing Active Directory

- When an Active Directory domain is first set up, it contains a default user account, administrator, and several default user groups.
- Here are some of the most important user groups:
  - **Domain admins** are the administrators of the AD domain. They are like root administrators, and possess incredible privileges and powers. You should never use this as your day-to-day account, instead opting for a domain controller account.
  - **Enterprise admins** are administrators, and have permissions to make changes that affect other domains in multi-domain forests. These should only be needed on rare occasions, like when an AD forest is being upgraded to a new version.
  - **Domain users** contain every user account in the domain.
  - **Domain computers** contains all computers joined to the domain, except domain controllers.
  - **Domain controllers** contains all domain controllers in the domain.
- If there are some administrative tasks that you need to perform a lot as a part of your day to day job but you don't need to have broad access to make changes in AD, then **delegation** is for you. 
  - Just like you can set NTFS DACLs to give accounts permission in the file system, you can set up ACLs on Active Directory objects.


### Managing Active Directory Users and Groups

The **Security Account Manager (SAM)** is a database in Windows that stores username and passwords. (This is where SamAccountName comes from.)

Everything you do in ADAC is actually done in PowerShell. 
- There's a "WINDOWS POWERSHELL HISTORY" pane, which shows the commands being run by ADAC.
- You can take an example like this and generalize it to create a script that can be used to repeat this process hundreds of thousands of times.
- To describe the full path of an object in AD, LDAP is often used.

There are two categories of group in AD:
- The most common one is called a **security group**
  - Security groups contain user accounts, computer accounts, and other security groups
  - The default groups (domain users, domain admins) are security groups
  - They're used to grant or deny access to IT resources
- The other type is a **distribution group**
  - A distribution group is only designed to group accounts and contacts for email communication
  - You can't use distribution groups for assigning permissions to resources.

Group scope has to do with the way that group definitions are replicated across domains.
- Keeping many large groups synchronized in a large network is a complicated problem;
- Active Directory uses group scopes to manage that complexity.
  - **Domain local:** This is used to assign permission to a resource.
  - **Global:** This is used to group accounts into a role.
  - **Universal:** This is used to group global roles in a forest.
    - Domain Local and Global groups aren't replicated outside of the domain they're defined in; but universal groups are.
    - Universal groups are replicated to all domains in a forest.


### Managing Active Directory User Passwords

- With certain exceptions, AD doesn't store user passwords -- it stores a one-way cryptographic hash of the password.
- If there's more than one person who can authenticate using the same username and password, then auditing becomes difficult or even impossible.
- To audit your infrastructure, in this sense, means to analyze who performed specific actions in your IT infrastructure.


### Joining an Active Directory Domain

Recall that joining a computer to Active Directory means two things:
1. AD knows about the computer and has provisioned an account for it;
2. The computer knows about the AD domain and authenticates with it.

A Windows computer that isn't joined to a domain is called a *workgroup computer*; the name comes from Windows workgroups, which are a collection of standalone computers that work together. Windows workgroups aren't centrally administrated, so they become harder and harder to manage as the network grows in size.

A computer can be in a domain or in a work group, but not at the same time.

Different versions of Active Directory are referred to as **functional levels**; an AD domain has a functional level that describes the features that it supports.


### What is a Group Policy?

**Group Policy Object (GPO)**: A set of policies and preferences that can be applied to a group of objects in the directory.
- **Policies** are settings that are reapplied every few minutes, and aren't meant to be changed even by the local administrators.
  - By default, policies are reapplied on the machine every 90 minutes.
- **Preferences** are settings that, in many cases, are meant to be a template for settings.
  - Someone using the computer can change the settings from what's defined in the policy, and that change won't be overwritten.

When you *link* a GPO, all of the computers or users under that domain, site, or OU will have that policy applied.

A GPO can contain computer configuration, user configuration, or both.

When a domain-joined computer or user signs into the domain by contacting a domain controller, that domain controller gives the computer a list of group policies it should apply.

When a domain-joined computer or user signs into the domain by contacting a domain controller, that domain controller gives the computer a list of group policies that it should apply. The computer then downloads those policies from a special folder called SYSVOL, that's exported as a network share from every domain controller. This folder's replicated between all of the domain controllers and can also contain things like log in and logoff scripts. Once the computer has downloaded its GPOs, it applies them to the computer.

Many policies and preferences in GPOs are represented as values in the Windows Registry. The **Windows Registry** is a hierarchical database of settings that Windows (and many Windows applications) use for storing configuration data.


### Group Policy Inheritance and Precedence

Precedence
RSOP


### Group Policy Troubleshooting

[ notes ]

### Mobile Device Management (MDM)

- MDM solutions will let you remote wipe a mobile device.
  - A **remote wipe** is a factory reset that you can trigger from your central MDM, rather than having to do it in person on the device.
- MDM policy settings are specific to each mobile OS; but these policies can be created and distributed using an **Enterprise Mobile Management (EMM)** system.


## OpenLDAP

### What is OpenLDAP?

OpenLDAP can be used on any operating system, including Windows, Linux, and MacOS.


### Managing OpenLDAP

- You can use the command line to manage OpenLDAP; but it's easier to setup phpLDAPadmin.
- To use command line tools, you need to use LDIF files.

[Content](#content)


-----------------------------------------------------------------------------------------Data Recovery & Backups----------------------------------------------------------------------------


# Data Recovery & Backups

## Planning for Data Recovery

### What is Data Recovery?

**Data recovery** is the process of trying to restore data after an unexpected event that results in data loss or corruption.

When an unexpected event occurs, your main objective is to resume normal operations as soon as possible, while minimizing the disruption to business functions.

The best way to be prepared for a data-loss event is to have a well-thought-out disaster plan and procedure in place.

Disaster plans should involve making regular backups of any and all critical data that's necessary for your ongoing business processes.

A **post-mortem** is a way for you to document any problems you discovered along the way; and most importantly, the ways you fixed them so you can make sure they don't happen again.


### Backing Up Your Data

Data you'll want to back up includes (but is not limited to):
- Email databases
- Sales databases
- Financial spreadsheets
- Server configurations
- Databases

#### Local storage
- Pros:
  - Data is physically nearby
  - Low bandwidth needs
- Cons:
  - Data loss due to damage at location

#### Off-site storage
- Pros:
  - Data is safer in multiple locations
- Cons: 
  - Needs security and encryption
  - Needs large amounts of bandwidth


### Backup Solutions

On-site/self-managed backups could be as simple as buying a commercial NAS device, loading it with a bunch of hard drives, and sending data to it over the network. Long term, this is not an optimal solution, however.

If your organization's budget allows, you should have on-site and off-site backups.

The standard medium for archival backup data storage is data tapes. They're much like audio cassette tapes, since they use spools of magnetic tape run through machines that allow data to be written to -- and read back from -- the tape.

**rsync** isn't explicitly a backup tool, but it's very commonly used as one. 
- It's a file transfer utility, designed to efficiently transfer and synchronize files between locations or computers.
- rsync supports compression
- You can use SSH to securely transfer data over a network
- Using SSH, it can also synchronize files between remote machines, making it useful for simple, automated backups.


Apple has a first-party backup solution, called **Time Machine**.
- It operates using an incremental backup system.

Microsoft offers a first-party solution called **Backup and Restore**. It has two modes of operation:
- A file-based version, where files are to a zip archive
  - Supports either complete backups or incremental ones;
- The system image, where the entire disk is saved block by block to a file
  - Supports differential mode, only backing up blocks on the disk that have changed since the last backup.


### Testing Backups

It's not sufficient just to set up regular backups -- you also need a recovery process, and that process needs to be tested regularly.

**Restoration procedures** should be documented and accessible so that anyone with the right access can restore operations when needed.

**Disaster recovery testing** involves documenting the procedure, regularly testing the documentation to ensure it works (now and in the future), and is a critical exercise that should happen once a year or so.


### Types of Backup

Ways to perform regular backups:
- Full backup
  - 
- Differential backup
  - 
- Regular incremental backups
  - 

While a differential backup backs **up** files that have been changed or created **since the last full backup**, an incremental backup is when only the data that's changed in files **since the last incremental backup** is backed up.

It's a good practice to perform infrequent full backups, while also doing more frequent differential backups.

Another thing backup systems can do to help save space is **file compression**.
- When creating a backup, all the files and folder structures will be copied and put into an archive.
  - Archives are useful for keeping files organized and preserving full structure.
- Compression is a mechanism of storing the same data while requiring less disk space, by using complex algorithms.

To store backup data on site, you can use a commercial NAS device; or configure a file server with a large amount of disk space.

**Redundant Array of Independent Disks (RAID)** is a method of taking multiple physical disks and combining them into one large virtual disk.
- RAID arrays are a great, inexpensive way of creating a lot of data capacity, while minimizing risk of data loss in the event of disk failure.
- They can also be flexible enough to allow future growth in disk capacity.

*RAID isn't a backup solution; it's a *data storage* solution.* A RAID array doesn't protect against accidentally deleting files, or malware corrupting your data. *RAID is not a replacement for backups.*


### User Backups

Ensuring reliable backups for client devices is a bit more challenging than infrastructure devices.

One common solution to user backups is to use a cloud service, such as Dropbox, Apple iCloud, and Google Drive.


## Disaster Recovery Plans

### What's a Disaster Recovery Plan?

A **disaster recovery plan** is a collection of documented procedures and plans on how to react and handle an emergency or disaster scenario, from the operational perspective.

The goal of the disaster recovery plan is to minimize disruption to business and IT operations, by keeping downtime of a system to a minimum and preventing significant data loss.

The plan actually covers preventive measures and detection measures, on top of the post-disaster recovery approach.

**Preventative measures** cover any procedures or systems in place that will proactively minimize the impact of a disaster. (This includes things like regular backups and redundant systems/power supplies.)

**Detection measures** are meant to alert you and your team that a disaster has occurred that can impact operations.

Other things that should be monitored to help head off any unexpected disasters include:
- Environmental sensors
- Flood sensors (in the server room)
- Temperature and humidity sensors (in the server room)
- Evacuation procedures

**Corrective or recovery measures** are those enacted after a disaster has occurred. (These measures involve steps like restoring lost data from backups or rebuilding and reconfiguring systems that were damaged.)

When one system in a redundant pair suffers a failure, it's called a **single point of failure.**


### Designing a Disaster Recovery Plan

- Perform Risk Assessment
  - A **risk assessment** allows you to prioritize certain aspects of the organizations that are more at risk if there's an unforeseen event.
- Determine Backup and Recovery Systems
  - Anything critical to operations should be made redundant whenever possible.
- Determine Detection & Alert Measures & Test Systems
- Determine Recovery Measures


## Post-Mortems

### What's a post-mortem?

- We create a **post-mortem** after an incident, an outage, or some event when something goes wrong, or at the end of a project to analyze how it went.
- The purpose of a most-mortem is to learn something from an event or project, not to punish anyone or highlight mistakes.


### Writing a post-mortem

- A typical post-mortem for an incident begins with a brief summary (just a short paragraph)
  - What the incident was
  - How long it lasted
  - What the impact was
  - How it was fixed
- Always clearly state the timezone to be clear while listing dates and times.
- Next is a detailed timeline of key events
  - The timeline should wrap up with the actions taken that resolved the outage and restored services, signaling the end of the event.
- Next, a very detailed and honest account of the root cause is covered.
  - What led to the issue
- A more detailed explanation of the resolution and recovery efforts should be documented next.
- Lastly, close out the report with a list of specific actions that should be taken to avoid the same scenario from happening again.

Analyzing *what went well* is just as important as what went wrong. Highlight failsafes and effectiveness of the system in place.



[Content](#content)