```{r, echo=FALSE}
 library(ggplot2)

 pal <- c(
   "Data Provider" = "#33a02c",
   "Third-Party" = "#a6cee3",
   "Researcher" = "#1f78b4",
   "Unrestricted" = "#a6cee3",
   "Restricted" = "#1f78b4",
   "Open" = "#1f78b4",
   "Low Security" = "#a6cee3",
   "Medium Security" = "#33a02c",
   "High Security" = "#b2df8a"
 )

plot <- function(data) {
   ggplot(data, aes(x=metrics,y=1)) +
   geom_bar(stat="identity", aes(fill=rank), width=1) +
   theme(axis.title.x=element_blank(),
         axis.text.x=element_blank(),
         axis.ticks.x=element_blank(),
         axis.title.y=element_blank(),
         axis.text.y=element_blank(),
         axis.ticks.y=element_blank(),
         legend.position = "none") +
   scale_fill_manual(values = pal) +
   geom_text(aes(label=paste(metrics,": ",rank)),
             color="black",
             position = position_stack(vjust=0.5)) +
   coord_flip() +
   theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank(),
         panel.background = element_blank())
}

knitr::opts_chunk$set(fig.width=4, fig.height=2) 

```

## Physically Protecting Sensitive Data

The physical protection of sensitive data is one of the key parameters that data custodians can and do influence. Within the Five Safes Framework, "safe settings" are heavily influenced by how data are physically protected. However, it is also the parameter that is most dependent on current technology. While sending around floppy disks to researchers who inserted them into desktop computers in a locked room, isolated from computer networks, was common in the 1980s, it has been superseded by technologies that provide similar or stronger security, combined with greater ease of access. 

Possibly because technological advances happen faster than legal or cultural habits change, we have found that  data custodians and policy makers may not always be aware of the most current technological possibilities when crafting the legal and contractual framework for data access. This chapter sets out to describe the currently available spectrum of physical protection methods. We use a framework that defines five dimensions with which we can characterise a particular access mechanism. We then describe several actual examples, both from the case studies in this handbook as well as others that we are aware of. Finally, we caution readers that by the time that this chapter is being read, the range of possibilities may yet again have expanded (rarely does it contract). Technological obsolescence is intrinsic to a chapter relying so heavily on technology.

### Five Dimensions of Physical Security

In any data sharing setup, the fundamental setup always involves the original holder of the data, and access by a new entity. In the context of this Handbook, the original holder is the data custodian, and the new accessor is the researcher. Technology determines how the physical exchange and access may happen. 

![Exchange of information](assets/images/custodian-researcher.png)

Here, we propose  five dimensions of physical data security to serve as a framework to evaluate the different defining features of various data access mechanisms. These are:

- the physical **location of analysis computers and the data**,
- the **control over analysis computers** that researchers are allowed, 
- the **location and type of access computers**, 
- the **level of security of  access locations**, and 
- the **range of analysis methods available** to researchers.

When proposing and negotiating a potential use sharing agreement, evaluating the physical security arrangements along these five dimensions can help researchers and their data providers craft robust mechanisms to protect data when transferring and using data for research. Importantly, these physical access mechanisms in turn interact with the other four safes. We highlight such interactions in the examples provided. 

For each dimension, classifications range from **1** to **3**, except for security, which has a range of **4**. 

####  Location of Analysis Computers and Data

The researcher-accessible administrative data can be stored at one of three types of locations. The data can remain with  the data provider, the data provider can transfer the data directly to the researcher, or the data provider can transfer the data to a trusted third party. Each possible data location comes with its own requirements, advantages, disadvantages, and special considerations for the researcher and data provider.

| 1 | 2 | 3 |
|---|---|---|
| Data provider | Third-party | Researcher |

Key consideration for the choice of location is the level of trust that the data provider has in the entity controlling the new location. The enforcement of DUA or MOU is key. Transferring control to another entity might be desirable when support for many researchers is a burden for the regular business of the data provider. For instance, by transferring the data to the researcher, a data provider may no longer be responsible for the cost of providing computational infrastructure for data storage and analysis. On the other hand, costs of enforcing access restrictions, such as site visits, may be higher once physical custody of the data has been transferred.

In certain cases, the transfer to a third party or the researcher unlocks the possibility of combining data from multiple data providers. For instance, government departments responsible for immigration and taxes may not be legally allowed to share data, but they may each be able to transfer the data to a national statistical office. Similarly, multiple companies may not be willing (or legally allowed) to share data with one another, but may be able to transfer the data to trusted third party. In other situations, one branch within a government department, responsible for enforcement, may transfer the data to another branch, whose business it becomes to make the data accessible. The advantages of this arrangement include having an organization that is more familiar with and responsive to the needs of the researchers handling the data as well as reducing the burden on staff and resources at the data provider. 

Note that the location of the data on its own in no way defines how researchers access the data, or the type of analysis a researcher can conduct. 

#### Control over Analysis Computers

Analysis computers are the computers on which researchers perform their analysis on and are by definition at in the same location as the data. They need not coincide with the  computers which researchers use to access the data. The level of control that researchers are allowed over these computers may differ widely. In some cases, the researcher may have physical control over the analysis computer, in others, even software control is minimal. Of key interest to many researchers is the  software that researchers can utilize.

| 1 | 2 | 3 |
|---|---|---|
| Low | Medium | High |

In the least restrictive arrangement, researchers can have full  access to the analysis computers, with no restriction on the software that researchers can use to perform their analysis. The researcher may own and physically control the analysis computer, such as  when the data is transferred to the researcher. Even when administrative control over the analysis computer is retained by the data provider or a third party, the researcher may be able to request and utilize their choice of software on the analysis computers without much restriction.

>  One example of this is the way that NCES restricted-use data licenses operate. The researcher must set up a secure data room in accordance with NCES requirements, but is otherwise free to utilize whatever software they want to analyze the data.

In other instances, researchers only have limited control over the analysis computers. This may occur in cases where researchers only have remote access to the analysis computers. Limitations can range from a white (allowed) list of software, with no restrictions on packages that can be installed to augment that software (e.g., Stata, R, Python), to a pre-approved list of software, which can only be modified via an approval and security vetting process. This may be due to technical requirements related to computer and network security, as a mechanism for disclosure control, or the expense of acquiring or maintaining multiple sets of software. These restrictions affect not only the base software itself, such Stata or R, but also third party packages for those software; while the base software itself may be unrestricted, additional packages not signed by the original developer may not be allowed. 

> The Federal Statistical Research Data Center network has a specific set of software that they make available to researchers, who must use one of the programs that the FSRDC has on their secure computing network. Additions must be approved by program managers and security analysts. 

> The Norwegian data access mechanism runs only a limited set of Python modules, with no additions allowed.

> The Canadian Remote Access Mechanism runs only a limited subset of SAS commands, with no exceptions allowed.


#### Location and Type of Access Computers

Access computers (end points) are the computers researchers utilize to access the data. In some cases, access computers are co-incidental with analysis computers. However, when data are not in the same location, access computers are distinct from analysis computers. Access computers can be located at and be owned by the data provider,  the researcher, or a third party institution. However, ownership is not necessarily aligned with location. For instance, a researcher may be assigned a computer that serves both as access and analysis computer, but which is owned by the data provider.

| 1 | 2 | 3 |
|---|---|---|
| Data provider | Third-party | Researcher |

If the access computer is located at the data provider or the third party (the *data access providers*), the researcher must travel to their location. This allows the data access providers maximum control over the access computer and its security arrangements, including physical monitoring, removing USB access ports, controlling user access to specific files and folders, and other measures. 

> Example: Bureau of Labor Statistics Research Data Center in Washington DC. (maybe some of the examples in Handbook)

Note that when the access computer is located with the third party, travel may still be required, but typically over shorter distances. 

> Example: NB. FSRDC (note that strictly speaking, FSRDC sites are under control of the US Census Bureau, but are located on university campuses or within other research institutions)

Access computers can be of several types. In some cases, the agreement may prescribe certain types of access computers, in others, they may remain undefined. When not further defined, a researcher may be able to use any computer for access, for instance, when access is via a secure website. VDI access, defined below, may be allowed from any computer capable of running the necessary software, including tablets. On the other hand, secure laptops with dedicated VPN setups and encrypted hard-drives may be deployed. In certain cases, dedicated thin clients, including zero-footprint thin clients, provide similar functionality as such dedicated laptops, without the computational capability that such laptops may have. As the enumeration of possibilities also makes clear: physical configuration control for such access computers may also differ widely. We discuss software configuration control below.

#### Security of Access Locations

The location of  access can have varying levels of security. We classify the levels of security into four levels, ranging from **open access** (no security) to **low, medium, and high** security arrangements. Unlike the other dimensions outlined above, these are not concrete distinctions between different mechanisms but rather broad classifications of the overall rigor of physical security regimes. Note that in some instances, specific rooms may be mandated, whereas the open access regime might not specify any specific location. 

| 1 | 2 | 3 | 4 |
|---|---|---|---|
| High| Medium | Low | Open |

An **open access** arrangement is one where there are no mandated controls on the physical location of the access computer. The access computer is protected only by hardware and software configuration of the device itself. This is typically seen in remote submission systems, such as the IAB JoSuA interface where there are no explicit restrictions on where the researcher can use the interface. Trivially, this may be true when access and analysis compture are coincident with the researcher's laptop. 

> Example: Access to IAB's Joshua can be from any internet connected computer, regardless of location. 

A **low security** arrangement has a mandated location for the access room or other basic security precautions, but otherwise has no access controls outside of the control of the researcher. Frequently this takes the form of provisions in the data use agreement between the data provider and researcher mandating certain steps such as storing the data in a locked room, but the security arrangements are maintained by the researcher. In some cases, the data provider explicitly reserves the right to approve the security arrangements, conduct audits, or otherwise directly verify that the researcher is in compliance with the security requirements or the access room.

> French CASD mandates that thin clients be deployed in university offices, although relaxations were allowed during the 2020 COVID-19 worldwide health crisis. (CITATION)

> The SFUSD-Stanford data use agreement template mandates that Stanford researchers take “reasonable and appropriate efforts” to keep the data “in a space otherwise physically and electronically secure from unauthorized access”. However, the district does not exercise physical control over the researchers’ access room security.

> The requirements for the data location outlined in the NCES restricted-use data license is an example of a medium security arrangement under the control of the researcher. The data must be kept in a locked room with access restricted only to licensed researchers, with the security arrangements subject to random audits by NCES.


An access room with a **medium security** setup has mandated security features. Access is restricted to approved researchers, with a minimum of a physically secured facility such as a locked room where only approved researchers have key or keycard access.  Frequently, medium security room setups will be under the control of a third party or the data provider itself. This enables the room administrator to directly monitor who has access to the room and the physical security of the access computers within the room.

> Example are the IAB thin clients in various locations, including in North America. These are in a room under the control of the research institution hosting the thin client, and are not freely accessible to the researcher. 

A **high security** access room has stronger specifications for physical security. This can include mandating that the room have secured walls that fully extend from the floor to ceiling with no gaps, electronic shielding for the room, video monitoring of the room, identity or biometric verification for people entering the room, and other security arrangements that extend beyond simple access controls for people entering the room. The NB-IRDT data centers, with their stringent access controls and additional physical safeguards such as bolting the server to the floor in a separate locked cage, falls into the high security category.



#### Analysis Methods

The range of analysis methods allowed by access systems can vary widely. Researchers may be able to leverage a wide range of analysis methods, ranging from simple tabulations to complex machine learning tasks. In other cases, they may be limited to a small set of methods, defined by the data custodian for technical or security reasons. Note that this dimension is distinct from the control that researchers have over software installation. A system may allow for any analysis method, as long as it is implemented in SAS - a situation where the software choices may be limited (and limiting for researchers), but where the analysis methods are nearly unrestricted. 

| 1 | 2 | 3 |
|---|---|---|
| Restrictive | Medium | Flexible |

Environments with unrestricted analysis methods allow researchers to utilize the full range of methods available in the set of software that is available on the analysis computer, subject to other restrictions on the analysis computer as discussed in the previous section. Limited analysis methods place restrictions on what researchers can do, such as limiting the language set available to researchers to a whitelisted set of commands.

> Norwegian system is limited both to Python, and within Python, to a limited set of analysis methods, a strict subset of the Pandas package.  

> IAB system only allows for Stata in Josua, but within Stata, few restrictions are imposed.

> Online tabulators. Can express many things as conditional tables, working through that interface you are limited to tables.

Economists don’t care so much about things like NCES public use data, but citizen access is valuable for tables and summary stats


### Technical features, infrastructure, implementations

#### Thin Clients

Thin clients are computers that have been optimized for connecting with remote servers that store the data and do the actual analysis. Very restrictive implementations of thin clients can prohibit any usage beyond displaying information from the server and accepting mouse and keyboard input from the user. One of the main advantages of dedicated hardware thin clients is that they are cheaper and simpler than regular computers. As of the time of writing, thin clients can cost as little as $100 for the hardware itself, in contrast with the cheapest entry level computers which are several hundred dollars. Note however that most thin clients require a server-side infrastructure to support both access and security updates. Thin clients typically operate without local storage, thus preventing users from saving data to the client.

For data providers and researchers setting up remote access to analysis computers via thin clients, the clients themselves do not need to be capable of running statistical software or intensive analysis; the analysis will occur on the server that hosts the data and software packages. Thin clients can either be provided directly to researchers or be housed within a research data center. Thin clients can be sourced from many manufacturers of enterprise hardware, both as standalone devices for the user to configure as well as full fledged hardware and software package solutions configured by the vendor.

> IMAGE of CASD thin client

> IMAGE of a commercial zero-footprint thin client

#### Biometric authentication (fingerprint, etc)

Biometrics are physical and biological features unique to individuals. Biometric authentication is the use of biometric features to verify the identity of individual users. By verifying the user’s identity based on stored information about authorized users, biometrics can be used to authenticate authorized access to access computers, analysis computers, and access rooms. The main components of such an access system includes the biometric sensor itself, which is connected to a database that contains the set of validated users, and controls either the physical or electronic lockouts for a given system (e.g. entering a room or logging into a computer).

Most biometric authentication techniques rely on the physical characteristics of individuals. One of the most common biometric technologies in current use is fingerprint scanners for consumer electronics such as laptops and smartphones. Other commonly used technologies include facial recognition, retinal or iris recognition, and voice identification. Biometric authentication techniques can serve both as a primary form of identification as well as being layered in two or multiple factor authentication techniques, such as in conjunction with passwords or other devices. When applied to physical data security, biometrics authentication can be required  by data providers as part of an access agreement, collected from authorized users, and implemented by any of the parties with administrative control over access rooms, access computers, and analysis computers as required.

#### Physical access cards

Physical access cards are electronic cards that identify the card bearer for a physical access control system. Access to devices or rooms are secured by a card reader validates the user’s card with a central database that has a set of valid cards and subsequently disables the locks on the system or room that it is protecting. The cards themselves can use magnetic stripes, barcodes, electronic fields, or other systems for interfacing with the card reader. Physical access cards are commonly used in universities and have the advantage of likely having existing infrastructure to support the creation of secure access rooms for researchers receiving administrative data.

#### Secure Rooms

Beyond access control, rooms can have various specifications for securing it against unauthorized access. For some secure rooms that house administrative data for research purposes, one requirement is having the room fully enclosed by walls that extend from floor to floor with a minimum number of possible entryways to minimize the possibility of unauthorized access. Any doors, windows, air vents, and other possible entryways would be secured by bars, mesh, or other methods to deter access. The doors and walls can have minimum specifications of construction materials, techniques, and thickness to increase protection against physical attacks; reinforced doors and walls offer increased protection compared to regular home and office construction materials. Door hinges, access panels, partitions, windows, and other possible ways of entering the room would be installed from the inside of the secure room to prevent their removal from the outside.  In instances where the room stores data itself, the devices within the room can be mandated to have no outside network connections (an air-gapped network), or no network connection at all

#### IP address restrictions

For remote access mechanisms, one way to ensure that only an authorized user has access to the remote system is to restrict the ||IP|| address of the devices that are allowed to connect to the server. There are two types of restrictions, blacklisting and whitelisting. Blacklisting specific addresses is used to block known or potential bad actors but otherwise does not restrict connections to the server; whitelisting only authorized users is the primary use of IP restrictions in an access control mechanism. This is frequently an option built into the software for managing the server. For example, software used for managing secure file transfer protocols can restrict the IP addresses that it will accept connections from. For data providers and researchers, this can be restricted to specific devices that the researcher registers with the data provider as the access computer.

#### VPN

Virtual private networks (VPN’s) are used to allow users to exchange data over public networks as if they were directly connected on a private network. VPNs utilize an encrypted channel established between the remote computer and the network to securely transfer data and gain access to resources on the network. Users must authenticate themselves, such as with usernames and passwords, to access the VPN. VPN’s has applications for transferring data to researchers as well as remotely accessing data by either the researcher themselves or from a remote data center. For open access settings VPNs can be particularly useful, as they allow the encryption (and therefore security) of any data that the researcher can access from a public network.

#### Remote desktop

> This needs a bit of cleaning up.

Remote desktop systems (also sometimes called Virtual Desktop Infrastructure, VDI) are software packages that enable users on one computer to connect to another computer over a network. These are conceptually the same as the software component of thin clients but can be installed on any computer; all modern Microsoft operating systems have had native remote desktop clients, and there are many implementations for other operating systems as well. Remote desktop software can be used to allow researchers to access an analysis computer or server under the control of the data holder, without needing to provide the researcher with a physical thin client. On the data provider side, the remote desktop service can be configured to prevent file transfers and copying data to the researcher’s computer.

#### On-site storage

There are many options for storing data on site for data providers and researchers. For researchers and data providers with robust IT infrastructure (e.g. Research 1 universities, national statistical agencies) there are generally internal guidelines and policies for data storage that render this a solved problem. For researchers and data providers without existing data storage policies and needing to set up their own storage systems as part of a data sharing agreement, the primary technical considerations are data loss prevention, storage device uptime, and security.

The annualized failure rate (the probability that a device will fail during a full year of use) of modern consumer-grade hard disks is typically below five percent, but generally does not get much below one percent. Depending on the risk tolerance of any particular researcher or data provider this single disk failure can be unacceptably high; technical solutions include using enterprise-grade disks with lower failure rates, using multiple disks in a mirrored array that guards against single or multiple disk failure, and implementing multiple backup copies of the data that can be quickly restored. A common strategy for backups is to have three copies of the data, with two backup copies stored on different devices, and with at least one copy stored off site. Backup strategies will need to be tailored to fit specific scenarios; for instance, off-site storage may be prohibited under data sharing agreements.

Maximizing system uptime for the data storage device is important for allowing the uninterrupted use of the research data. In the simplest implementation of storing data on individual computers with directly attached storage, any issue with the system will result in the interruption of data transfer or research activities. Specially built storage servers allow for maintenance, including hot-swapping storage drives, while the server remains running. Prospective data centers can also set up multiple storage servers to run in parallel with the data mirrored between them, using one or the other as necessary to balance usage and take servers offline for maintenance as needed.

Security in the context of setting up data storage is the prevention of unauthorized access to the data. No solution is ever without risk, although risk can be reduced with the proper safeguards. The proper configuration and maintenance of the storage device is key in preventing unauthorized access to the data. For instance, the Equifax data breach in 2017 was a result of Equifax failing to apply a security patch for a known vulnerability of the software that Equifax utilized for its website; the software vendor had already released a patch when the breach occurred yet Equifax had neglected to deploy the update. In addition to properly applying security updates and configuring access, the encryption of the data on the server can provide the final line of defense in the event that an adversary does get access to the server. This can protect against both unauthorized remote access via software vulnerabilities or physical access where the storage device itself is compromised.

#### Cloud storage

In lieu of maintaining storage systems on site, utilizing a cloud storage service is an alternative for data providers and researchers looking to store large amounts of data. Cloud storage providers, such as through Google Drive, Dropbox, Box, Microsoft OneDrive, and other vendors, manage the physical infrastructure and allocate storage space to the user on an as needed (and contracted) basis. This saves the user the capital costs and technical expertise required to set up their own on-site storage, but comes with the tradeoff of placing the data under the control of a third party. Cloud services by definition require and enable remote access to data, which may prohibit the use of cloud storage under some data sharing agreements. However, many research universities have agreements with cloud service providers in the acknowledgement that the scalability of the storage solution and the resources for security that major cloud services providers can provide outweigh the benefits of maintaining their own storage on site.

---

### Typical access mechanisms

#### Remote Execution

Under a remote execution model, data is stored remotely in a location such that a researcher does not have direct access to the data. In this scenario, a researcher needs to submit a request to have the data provider run the analysis on behalf of the researcher and share only the summary output, with the researcher never having access to the actual data.

Remote execution requires that a data provider maintain dedicated staff with the technical expertise to interface with researchers, run the researchers’ analysis, and check the output for data anonymity before sending it back to the researchers. The systems to perform the analysis and disclosure checks can be manual or automatic, which both require technical experts to maintain.

The data provider also needs to create and maintain the systems to facilitate the transfer of the necessary files (researchers need to receive the synthetic data, submit analysis files, and receive the output) as well as to allow the data provider to run the necessary analysis on behalf of the researcher.

A key requirement for such a system is the provision of accurate codebooks and documentation from data providers to researchers such that they can prepare the appropriate data request and analysis files for the data provider. While important for all data exchanges, this is especially important for remote execution since researchers cannot personally examine the data. One common method is for the data provider to give researchers synthetic data files that have the same variables and table structures as the real data, but have fictitious values for the variables.

By maintaining full control of the data as well as having the opportunity to check the researchers’ request and check the output before handing it back to the researcher, remote execution gives the data provider the highest level of data security. The primary tradeoff is the additional resources required on the part of the data provider to perform these tasks and the additional time it will take for a government to receive relevant results from their research partner.

One example of a national statistical agency that uses a remote execution model is Statistics Canada, which allows researchers to submit analysis code after testing it on synthetic data for a select number of their databases. The Statistics Canada implementation follows the standard remote execution model. Similarly, the German IAB has a remote execution portal where researchers can test their code on test data data and upload their code for execution, and only access approved results when their job is complete.

A variant on the remote execution model is the United States National Center for Health Statistics Research Data Centers, which requires researchers to first submit their analysis code for manual approval before arriving at the research data center itself to run the analysis.

#### Physical Data Enclave

In a physical data enclave, researchers must physically enter the data enclave to access the data and run their analysis code. The data provider can choose to store the data either on site at the data enclave itself, or store the data on a remote server that can only be accessed by specifically configured computers located within the data enclave. In either case researchers only have access to the data in a secure and physically controlled environment.

To run a physical data enclave, a data provider needs to have an access-controlled space for researchers to work in with the requisite servers, computers, and software packages. The data provider must also have staff or automated systems to ensure that researchers are not running proscribed analyses and checking the outputs before being removed from the physical data enclave.

The data provider gets most of the security benefits of remote execution by maintaining full control over the data in the entire research process. It removes the potential bottleneck and additional expense of requiring dedicated staff on the part of the data provider to actually run the analysis on behalf of the researcher. The ability of researchers to personally examine the data in controlled settings enables them to potentially work with data providers on improving data quality in such a setting.

However, physical data enclaves still impose restrictions on the flexibility of researchers and the speed at which governments can receive research findings; instead of waiting for someone to run the remote execution for them, researchers have to schedule visits to a physical location. It also requires the data provider to provide the physical and technical infrastructure for researchers to conduct their research in a secure location.

Different models of physical data enclaves exist. The traditional model in the United States is the Federal Statistical Research Data Center (FSRDC) network, where federal statistical agencies partner with research institutions to provide secure data access facilities managed by the US Census Bureau. Research institutions maintain the data enclave itself and the client computers within the data enclaves, which are connected to servers maintained by statistical agencies. Researchers must be approved by the Census Bureau and pass background checks before gaining access to the facility and data, and the output is subject to disclosure-avoidance review by FSRDC staff. FSRDC type facilities represent the highest level of security for protecting sensitive data, but are also more expensive than other methods which rely more on trust and less on physical security. Initial startup costs could reach hundreds of thousands to millions of dollars, and ongoing operating costs, while much lower, must cover full time staff and maintenance on the equipment.

An innovation on the physical data enclave is the SafePod network in the United Kingdom, which scales down a full-scale research data center. The SafePod has much lower installation costs than a full data center, around £25,000. It is a standardized, prefabricated unit that can be placed in any partner institution, and the pod itself serves as the physically controlled space. Like a FSRDC, a SafePod facilitates researcher access to data stored on statistical agency servers; in this case, with access to the data approved by the actual data providers while the partner institution handles local support and physical access controls. While the SafePod is still a physical location that requires installation and ongoing staff and maintenance, it is an example of innovation in physical data enclaves that makes this highest level of data security less costly.

#### Virtual Data Enclave

A virtual data enclave is conceptually similar to physical data enclaves, except there is no physically controlled space that the researcher must visit in order to access the data. Rather, researchers utilize different technical means to remotely access servers that store data and perform their analysis on the remote server. Software access controls perform automated scans of the output and prevent the researcher from removing data from the remote server.

Data providers using a virtual data enclave model maintain the servers that house the data and enable researchers to run their analysis, the connections with the thin clients and the remote desktops used to connect with the server. A virtual data enclave includes trained staff, who help process data and assist researchers. There are two basic approaches to the remote access mechanism: either using remote desktop software that the researcher can install on their own computer, or a dedicated computer (referred to as thin clients) that the data provider loans the researcher to connect to the server. To address physical security concerns, data providers can impose storage and safety requirements on researchers as part of the agreement that allows them access to the virtual data enclave or have dedicated staff conduct periodic audits.

The virtual data enclave model has a major advantage for researchers in that they no longer have to travel to specific facilities to perform their research. Furthermore, instead of the cost of maintaining an entire physical data enclave and the associated staff at each enclave, the data provider only needs to provide researchers with the necessary thin clients or remote desktop systems and can centralize their data staff.

The primary tradeoff is the slightly lower level of data security when the researcher accesses the data, as the data provider relies on only software level controls without the ability to physically check the researcher and their output as in a physical data enclave. However, with the proper implementation this level of security is still quite robust and less costly.

Statistics Denmark is one major statistical agency that uses a virtual data enclave model for access to their data. Researchers approved by Statistics Denmark can utilize specific client software for remote access to servers that house research data and perform their analysis through the client software. Researchers must sign agreements with Statistics Denmark with specific requirements to protect the physical security of the terminal that they use to access the server, consent to having their transactions on the server logged to prevent unauthorized copying of data, and ensure that they do not identify individual persons or enterprises in their output.

#### Researcher-Provided Infrastructure

In some data sharing arrangements, the data provider has the researcher provide the data storage, access, and analysis infrastructure. The data provider will provide the data to the researcher, who has custodianship over the data.

Data providers must ensure that they properly remove variables containing personally identifying information from data that they transfer to researchers in order to protect the privacy of study participants. In the instance that researchers have access to potentially identifiable data, the data provider must take care to ensure that the results produced for publication do not contain personally identifiable information. The data provider and researcher must have the technical means to securely transfer the data. Many such tools exist, including commercial enterprise level cloud services such as Google Drive, Box, and Dropbox that can be configured for secure data storage and transfer.

This process allows researchers significantly more flexibility and rapid turnarounds on research findings of importance to their government partners. Allowing researchers to store the data on their own devices may reduce the burden on data providers, who only have to provide the data itself and the staff necessary to transfer it to the researchers. On the other hand, data providers may also choose to conduct random on site inspections or have researchers submit their output for approval, which requires staff time. In instances where researchers can work very closely with the data providers’ technical staff with direct access to their data, they can also help the government learn more about their data and improve processes and systems at the government.

Many research projects and data providers utilize data transfers to researchers, particularly among smaller scale data providers for whom a more expensive data enclave model is less feasible. For example, San Francisco Unified School District has a long-standing partnership with Stanford University, where the Center for Education Policy Analysis (CEPA) at Stanford acts as a data warehouse for individual-level administrative data on behalf of the district. While many of the researchers who use the data are affiliated with CEPA, the CEPA has dedicated staff with no ties to specific research projects to manage the warehouse. The district approves researchers and projects to have access to the data, while the warehouse performs data cleaning, anonymization, and ultimately provides data files to the researcher.

Large scale implementations of the data transfer model for sensitive, individual-level data also exist. The U.S. National Center for Education Statistics maintains a restricted-use data license model that requires researchers to set up their own version of a physical enclave, at their home location, as a requirement for becoming a license holder. The researcher must maintain an access-controlled secure data room with specific physical and electronic protection requirements and must undergo random NCES audits to ensure compliance with these procedures. The data is transferred to the researcher via encrypted disks with the passwords sent separately, such that the data is protected in transit and only the researcher with both the data disk and password can access the data. Combining the efficiency of data transfer with the increased security of physical and electronic protection shows how data access can be tailored for individual circumstances based on sensitivity and cost needs.

### Examples from the handbook along the five metrics

In this section, we explore how the five dimensions map onto the case study chapters in the handbook. Each set of data providers and researchers utilizes a unique combination of the five metrics for their data sharing framework.

#### SFUSD-Stanford

```{r, echo=FALSE}
sfusd = data.frame(metrics=c("Data Location","Access Computer","Analysis Computer","Access Room","Analysis Method"),
                  rank=c("Researcher","Researcher","Researcher","Low Security","Unrestricted"))

plot(data=sfusd)

```

In the SFUSD-Stanford Partnership, the data location of the full set of data that is available for research usage is the CEPA Data Warehouse, a third party organization. The warehouse serves as a trusted data service that ultimately transfers a restricted set of data to the researcher. The analysis and access computers are both under the administrative control of the researcher, with the data and analysis software on the same device. These devices are subject to Stanford and SFUSD requirements for data security, including enterprise operating system management and whole disk encryption for any device that holds the data. The access rooms are low security; researchers must take reasonable measures to physically protect the data but there are no specific requirements or checks on the location of the data itself. Typically this takes the form of storing the researcher’s computer in a locked office, although in the case of graduate student researchers the offices may be shared. The analysis methods are unrestricted, with researchers being able to use any set of statistical software that they can acquire for analysis.

#### New Brunswick

```{r, echo=FALSE}
nbirdt = data.frame(metrics=c("Data Location","Access Computer","Analysis Computer","Access Room","Analysis Method"),
                  rank=c("Third-Party","Third-Party","Third-Party","High Security","Restricted"))
plot(data=nbirdt)
```

The NB-IRDT serves as a third-party data center for the various data providers that supply it with data to make available to researchers. The data location, access computers, and analysis computers are all located on site at NB-IRDT facilities. Researchers use workstations to remotely access data from a central server, and store their data on a local server at the specific facility that the researcher is at. Researchers have partial access to analysis computers, without the ability to  Researchers have limited access to the access computer, with stringent security requirements placed upon their usage of the research workstation. The access room is under high security, with strong specifications of security such as restricting mobile devices and outside materials, physical controls on the servers and workstations, and having dedicated fiber optics cables to handle data connections between the central and satellite locations. [Missing information about access computer software and analysis methods from chapter]

#### IAB

```{r, echo=FALSE}
iab1 = data.frame(metrics=c("Data Location","Access Computer","Analysis Computer","Access Room","Analysis Method"),
                  rank=c("Data Provider","Third-Party","Data Provider","High Security","Restricted"))
plot(data=iab1)
```

The IAB uses three different access models, each with its unique implementation of the five metrics of data security. The most restrictive access method is the IAB on-site access method, where researchers must go to an affiliated research data center. In this model, the data location and analysis computers are both located at the IAB. Researchers have restricted access to the analysis computers, including not being allowed to install their own software. The access computers are located at RDC’s under the control of the IAB itself or third-party partner institutions, consisting of secured workstations at RDC-IAB and thin clients at its partner institutions. The analysis methods are limited to the statistical software packages available at the specific RDC. The room security depends on the specific RDC, although all RDC’s generally have strong physical specifications for security with additional restrictions beyond just access controls managed by the RDC administrator.

```{r, echo=FALSE}
iab2 = data.frame(metrics=c("Data Location","Access Computer","Analysis Computer","Access Room","Analysis Method"),
                  rank=c("Data Provider","Researcher","Data Provider","Open","Restricted"))
plot(data=iab2)
```

For IAB remote execution, the data location and analysis computers are both still under the control of the IAB. Analysis methods are limited to preparing program code on test data to run on the analysis computers at the IAB. However, the access computer is the researcher’s own device utilizing the JoSuA portal to submit requests to the IAB. The access room is open with no security requirements, as the researchers are limited to the deidentified output from the JoSuA system. 

```{r, echo=FALSE}
iab3 = data.frame(metrics=c("Data Location","Access Computer","Analysis Computer","Access Room","Analysis Method"),
                  rank=c("Researcher","Researcher","Researcher","Medium Security","Unrestricted"))
plot(data=iab3)
```

The IAB also makes anonymized data products available for direct download by researchers. In this instance, the data location, acces, and analysis computers are at the researcher’s institution, with researchers having full administrative control over the computer systems. As a result of that, they have the full range of analysis methods available as well. The IAB data use agreement for downloading the scientific use files specifics medium security requirements, with the building and room required to have some level of access control or monitoring against unauthorized access; options range from receptionists and security guards to admission simple key locks. There are additional requirements for electronic security such as encrypting the computers and servers with access to the data.

#### OLDA

```{r, echo=FALSE}
olda = data.frame(metrics=c("Data Location","Access Computer","Analysis Computer","Access Room","Analysis Method"),
                  rank=c("Researcher","Researcher","Researcher","Low Security","Unrestricted"))
plot(data=olda)
```

The Ohio Longitudinal Data Archive is a third party organization that provides data to researchers on behalf of the government. The data is initially located at the third party institution before ultimately being transferred to researchers via a secure FTP server. The researchers have full control over the analysis and access computer, which is required to be a desktop computer located in the researcher’s office space. This is a low specification of access room security, placing no additional requirements beyond utilizing a specific space. Researchers have full analysis methods available for them. Data can be provided in a variety of formats, including CSV files that enable the researcher to use any analysis software or method of their choosing.

#### Aurora Healthcare

The researchers for this project received data from the data provider via a secure file transfer protocol. The data location, acces computer, and analysis computers were all located at the researcher’s home institution. [need more info from Amy and Laura]

#### Cape Town

In the Cape Town partnership, the data was transferred from the data provider to the researcher. As such, the data location, access, and analysis computers are all with the researcher, with the researcher having a full range of analysis methods available. [need more information about access rooms, some more detail about how they did the transfer and storage etc]

### Other examples along the five metrics

#### FSRDC

#### Safepod

#### French

#### National Center for Education Statistics Restricted Use Data License

The National Center for Education Statistics (NCES), a part of the United States Department of Education, allows researchers to apply for a restricted use data license to store data on site at the researcher. The data location, access computer, and analysis computers are all under the control of the researcher, with specific security requirements for the computers, the storage mediums that researchers receive the data on, and any physical documentation. With full administrative control of the analysis computers, researchers also have no restrictions on the analysis methods that they are allowed to use. NCES mandates a medium level of security for the access room, specifying that it must be a locked room with access restricted to authorized users. The security arrangements must be approved by NCES prior to the receipt of restricted use data and are subject to unannounced inspections. 

#### Bureau of Labor Statistics Onsite Access

The Bureau of Labor Statistics (BLS) has two research data centers in its national office at Washington D.C. for access to particularly sensitive research files and surveys that are not available offsite or through the FSRDC network. The data location, access computers, and analysis computers are all located and controlled by BLS. As with other research data centers, there is a high specification of security for the access room, with access limited to approved researchers and all materials subject to search when entering or exiting the facility. Analysis methods are restricted to pre-installed versions of SAS, Stata, and SPSS, with limited use of approved statistical software and data files that can be installed by the BLS staff.

#### NCHS

[https://www.cdc.gov/rdc/b2accessmod/ACs200.htm - remote access no longer available, otherwise available at NCHS RDC or FSRDCs, not sure about the utility of "yet another RDC" example]