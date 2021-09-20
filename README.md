
## Identity on Demand: Implementing User-Centric

## Host Hub with Automated Shared Banking

## Experience

## 20th September, 2021

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/1.png)

## Members-

## ○ Amardeep Saha

## ○ Dev Pant

## ○ Devesh Kashyap


## Introduction to Problem

Banking is a multi-billion dollar industry that is suffering from the complex problem of
financial and economic stagnation. There are variousreasons for economic stagnation
such as non-performing loans, financial exclusion,liquidity trap, reduced cash flow,
fallacious government policies, and many more.

While problems such as erroneous government policiesare intrinsic, other problems such
as financial exclusion, reduced cash flow, and non-performingloans can be resolved by
upgrading the banks’ legacy systems and adopting moderntechnologies.

One such technological advancement which can be utilizedby the banking industry to solve
the above problems is “Open Banking “. It providesthird-party financial service providers
open access to consumer banking, transaction, andother financial data from banks and
non-bankfinancial institutions through the use ofApplication Programming Interfaces
(API).

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/2.png)

Although, open banking is a revolutionary idea it’sstill in its nascent stage due to many
unsolved technical issues such as the absence of transparentand user-friendly **Strong**


**Customer Authentication** (SCA) protocol for identity management, lack of proper
infrastructure for secure networking among differentbanks’ open APIs’, and many more.

Also without a proper ‘Universal user profile forbanking’, establishing connections with
already existing Open banking APIs is quite troublesomefor a user, decreasing the
experience in shared banking. Moreover, another problemfor customers includes
physically providing documents repeatedly for openingnew accounts in other banks for
the same individual which is vulnerable to theft/mishandlingcausing a delay in the
workflow. Along with it, the presence of a universaluser profile can also lead to the
implementation of various business models such asinstantaneous loan and fixed deposit
migration which is not possible in legacy bankingsystems.

## Solution

We propose to develop a high-level third-party applicationthat can initiate secure
communication among various banks’ open APIs whilesolving the problem of on-demand
identity management along with removing the issuerelated to security in open banking
systems.

This application will be providing users with a uniqueand universal identity that is
recognized in the banking market globally and canbe used as the identity on demand
verified by the first login into an open banking APIconnected with our app. This will
generate the profile key and decentralize this informationthroughout the network in a
secure manner.

This app will connect to bank APIs which are connectedto the decentralized networks. The
decentralized database will be available to otherpartner banks but its access will be given
only when the individual provides his/her key to therequesting bank. Once the key is
obtained by the banks, they can use the account informationto decide whether to grant
the requested service to the individual or not. Ifthe bank declined the request, the key will
be simultaneously updated and the bank will not beable to view the data again. If the
individual applying the request doesn’t have an accountin the accepting bank, the bank
may ask for the public key for accessing the necessarydocuments from the parallel
decentralized network having the documents to openthe individual’s new bank account.


A surface overview for the solution idea which we are proposing can be explained by the
diagram shown below.

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/3.png)

```
High-Level Architecture Overview
```
## Methodology

In this project, we will develop a high-level customizablethird-party application that can
initiate secure communication among various banks’open APIs through a novel blockchain
infrastructure and utilize its cryptographic capabilitiesto secure the process. Moreover, the


consensus algorithm with a multiparty signatory system will be used in tandem with our
open-source infrastructure to establish an identityon demand.

To keep our project as pragmatic as possible, we willbe assuming that the banks are using
the **PSD2 Open API** (as it is the widely used standardAPI in the open banking industry).

Keeping the above point in mind our API will followthe PSD2 API specifications mentioned
below to as much extent as possible:

- Read/Write Specifications
- Open Data API Specifications
- Directory Specifications
- Dynamic Client Registration Specifications
- MI Reporting Specifications

Moreover, we will also be introducing some changesin the bank’s open API which will be
used to facilitate the process of collateral informationtransfer, and new account creation.

## Technical Implementation

Due to the vast scope of our project, we have dividedour project into the following parts,
which will be explained subsequently with a dummydemonstration -

- Setting up our API and establishing connections andpermissions among the
    various nodes/clusters(banks)
- Integrating our API with the individual bank’s API
- Integrating and facilitating inter-bank operabilityand solving the
    identity-on-demand problem
- Collateral transfer and subsequent loan transfer provision
- Fixed deposit transfer provision

For our demonstration, we will be establishing a dummyconnection between 3 banks and
our API. Moreover, to explain the concept of loanand fixed deposit migration we will be
creating a dummy account and visualizing interbanktransactions.


### Establishing the Blockchain

Keeping the above requirements in mind, we decidedto use the blockchain framework of
**Hyperledger Iroha** for both the identity-on-demandand interbank communication
processes. Hyperledger Iroha is generally used forapplications such as interbank
settlement, central bank digital currencies, paymentsystems, national IDs, and logistics,
among others. Hyperledger Iroha uses YAC (Yet AnotherConsensus Mechanism) for
validation of the blocks.

Regarding our project, Iroha will function as theintermediary which will aid the
communication process while establishing an identityfor digital assets. Moreover, the
various permissions and roles available in HyperledgerIroha will help in establishing the
correct transfer protocols. Additionally, the featureof multi-party signatures while fulfilling
the quorum required will hugely aid in the securetransfer process.

Last but not the least, Hyperledger Iroha is open-sourcesoftware under Linux Foundation
which was developed to power industry-scale blockchainsolutions and has extensive
developer support for any problems incurred.

_Demonstration:_

For our demonstration, we have built a small scalenetwork consisting of 4 peer nodes
(banks) and 2 customers (CUSTOMER_1 & CUSTOMER_2)shown in the docker-compose file
below:

**Docker YML Code** :docker-compose.yml

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/7.png)

After the establishment of the dummy network, the genesis block for a sample node that
dictates the account creation process, transfer protocol,and rights will look like:

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/4.png)

After the creation of the genesis block, we can addmultiple accounts(users) at a time by
giving special permission to bank nodes for accountcreation with quorum 0. Once all the
accounts for a bank have been updated, interbank communication can happen through
these nodes with the pre-initialized set of protocols.

The accountability of the individual banks is reinstatedby the fact that every transaction
with a quorum greater than 0, will be recorded inthe ledger. Since the ledger is immutable,
any future transaction could be easily mapped to itsorigin. This inherent mechanism of
Hyperledger Iroha prevents the creation of fake accountsand hence makes the whole
banking process transparent and answerable.

### Inter-Bank Operatibility & Solving Identity-On-DemandProblem

After individual bank nodes have been set up and customers’account information has
been migrated into the permissioned blockchain whilerecording the information in the
immutable ledger, the bank nodes are ready for interbanktransactions.

For every transaction which takes place between 2banks or any bank & our API, it would
require 2 signatures to sign off the transaction andthen be recorded in the ledger. For
security, we are planning to make our API, such thatafter each session, the key pairs
between our API and bank nodes get refreshed, butmore on that later.

These recorded transactions will be stored in a chainwhich will be stored among the bank
nodes. But, even though the data will be shared itwill be intangible unless the correct keys
are provided by bank nodes for data retrieval andverification. This way the transactions
are secured while maintaining transparency in thesystem. This is the true essence of open
banking and blockchain which enables such dichotomyto happen.

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/5.png)

```
Communication Between 2 Nodes in the System
```

Now, regarding the “Identity-on-demand” application in our project, this problem will be
faced by the customer when he wants to migrate andopen a bank account in a new bank
registered in our network. By solving this problem,we can aid the customers viewing our
application to open their new bank accounts and transfertheir assets/loans/collaterals
from one bank to another.

Interestingly enough, this problem can also be solvedthrough Hyperledger Iroha. We can
establish the digital identity of a person which canbe used by all the banks in the network
if and when the person wants to open a new bank account.The process of establishing
digital identity is very similar to the process ofstoring assets depicted above in the
demonstration. The customer has to go through thetraditional KYC process once in any
bank in the network, which will store his credentialand establish his digital identity which
can later be used by any bank in the network afterproper authorization and
authentication.

### Loan Transfer and Fixed Deposit Transfer MigrationProvision

Now that we have established our network and solvedthe identity-on-demand problem we
can go ahead and add the loan and fixed deposit migrationfeature to our system.

Before diving deep into the technical implementationfor these features we have to
understand the overall migration process from a bird’seye view. Our application will
function as a platform for viewing the bank detailsof the user among his various bank
accounts in the network and provide deep insightsfor migration advantages to the user.

The overall procedure of displaying information andmigrating is displayed below:

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/10.png)

```
In the above process flow, it’s assumed that the user has a bank account in both the banks
and so the migration can take place smoothly. However,if the user doesn’t have an account
in the second bank, the concept of identity-on-demandwill be used and the second
account will be created by first asserting the user’sdigital identity through the processes
mentioned later in the Integration phase, then transferringthe relevant information to the
second bank for account creation and subsequent migration.
In technical terms first, our API interacts with thevarious bank APIs to extract user’s
account information through HTTP requests while datais being shared in JSON format,
then if the user opts to view migration options, ourAPI hits the AWS server where our API’s
peer node is located, which further extracts the requiredinformation while obscuring
user’s personal information from the first bank’speer node, and sends it to other banks’
peer nodes who analyze the information and send backnew loan options calculated by
them. These processes occur simultaneously among variousbanks in the network utilizing
the principle of multithreading, resulting in a fasterspeed. Moreover, each transfer process
requires the fulfillment of a signatory quorum of2 bank peers nodes in question to make
the information comprehensible. Without fulfillmentof the quorum, the information would
just be a double hash of the main information makingit highly indecipherable by the third
party without the correct key.
```
### Integrating the pipeline

First and foremost, let us first discuss how a normalweb/mobile application works. So, normally
when the users access the application, they use aweb browser/ android SDK that interacts with
a central server over the network. All the code forthe app lives inside the central server and the
data is housed inside a central database. Wheneverthey use the application they must directly
interact with the central server. This presents afew problems, the application creators could
change the application code on the server, or thedatabase at any time because they have full
control. The presence of central authority over thenetwork would be a major security concern
considering all the sensitive information travelingfrom banks to customers or vice versa via our
application.

This can be eliminated by using the blockchain networkwe have discussed above. We can use
our application to interact directly with the hyperledgerIroha network by putting out simple
HTTP requests each time any information needs to beaccessed. Providing a high degree of
network fault tolerance through the chain-based ByzantineFault Tolerant consensus algorithm.
This will increase the data throughput while supportingmore nodes, and effectively reducing the
consensus delay and the latency between nodes.


Our basic application model will be around a simple identity management toolkit built using a
standard javascript codebase. This will be securedwith an inbuilt app lock that can be a
one-time set key or fingerprint access. Once loggedin, the user will be prompted to create a
username, password (initially, which will be continuedlater on unless logged out)

![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/9.png)

After the security login to the app, the user willbe shown their profile with their unique universal
keycode and the list of all the Open Bank APIs. Oncethey select to visit their account with our
API a new set of private and public keys will begenerated corresponding to their bank accounts
which will be refreshed for each new sessionusingthe previous session’s key as an
argument. This will add another layer of securityto our application.

```
Demonstration: For our small-scale network with 4peer nodes and 2 customers, the python
program shown below will be used.
```
![](https://github.com/Sigsev-Dev/user_centric_host_hub_with_blockchain/blob/main/Images/8.png)

This can lead to a highly secured connection in addition to the database being decentralized
with hyperledger Iroha which will greatly reduce theattack vector in case of cyber attack.

flag==0

```
UI for Key Pair
```
The application’s interface will provide users withmultiple banking options, idling through
the financial transactions, loans, and offers. Throughoutthe whole pipeline, we will be
using some basic applications: Ionic Cordova, nodejs,npm, docker, docker-compose plus
Java, and the Android SDK Tools to compile the application.

The whole codebase for the android app can be clonedinto a local server. Installing the
npm packages, we can then run the Iroha instance usingthe docker commands, with a
demo implementation already explained above. We canfinally compile our Android mobile
App with ionic Cordova build commands.

#### UI Wireframe


## How useful our model is

Our project is the first of its kind with immensepotential to revolutionize the modern banking
experience. The promise of flexibility and conveniencecoupled with transparency and security
make our application quite conspicuous to existingand new customers alike. The user-centric
methodology adopted in our application makes it veryeasy to set up and use.

The problem of loan and fixed deposit
migration that we chose to solve is very
prominent ignored mainly due to
technological constraints. First and foremost,
in the present banking scenario, there is no
option for interbank fixed deposit migration
and the process of loan migration is very time
and labor-intensive as shown in the diagram.
The countless procedures and
documentation required for such migration in
the legacy banking system make it appalling
to the customers. Using our application
reduces the time required for migration from 2

- 3 weeks to a matter of minutes.

Furthermore, the use of our application
provides the following benefits to the banks:

- **Increased consumer base** :

```
The use of modern technology and
the convenience attained from their
use will attract more customers to the
bank, hence increasing the bank’s
consumer base
Present Loan Migration System
```

- **Increase in deposits** :

```
With the increase in consumer base, the cash flowwill surge in the system. More
customers will start depositing money in the searchof better profits, which in
turn will increase the bank's revenue.
```
- **Improved banking experience to customers** :

```
With the integration of a single interface, customerscan now have access to
multiple accounts in one place. Adding an overviewof their current financial
positions gives the customer the leverage to makequick credit decisions and
avail the best deals possible. The use of modern technologywill provide an edge
over other banking services which in turn will increasecustomer satisfaction
levels.
```
- **The reduced problem of Non Performing Assets** :

```
The issue of Non-Performing Assets (NPA) is very prevalentin developing
nations such as India. Moreover, the onslaught ofthe COVID pandemic has
further aggravated the condition. By employing oursystem, the regular checks
and the automated nature of the system will greatlyreduce the problem. Even
during the process of loan migration, banks can verifythe authenticity of
collateral without employing any extra manpower byusing our system.
```
- **Decrease in fraudulent deposits and money laundering** :

```
The increased accountability due to immutable distributedledger and the
provenance established to each bank account will hugelydecrease money
laundering and fraudulent deposits when our systemis employed. Moreover, this
transparency will create a secure corruption-freeenvironment for the customers
to operate in.
```
- **Redundancy of call centers and third-party agentsfor loan migration advertisements:**

```
There will no longer be any use of intermediariessuch as call centers and
third-party agents for loan migration advertisementsif our system is employed. If
any customer feels the need for migration, he candirectly access our application
```

```
and view the available options thus making call centers/third party agents
redundant.
```
Using our application on an industrial scale has hugebenefits for both customers and banks as
explained above. Moreover, due to the intrinsic natureof the tech stack used our application can
be easily scalable making it an ideal modern solution

## Societal impact and Future scope

### Societal impact

**1. Financial inclusion:**
    Loan and FD migration are banking activities thatare hidden in plain sight as they are not
    used frequently as the people who apply for it areprivileged individuals or individuals
    who have researched quite a bit about banking andare ready to go through the hassle as
    not all banks agree upon are migrating or the individualdoesn’t have a count in the
    agreeing bank. Our app aims to bring the concept ofmigration into the limelight so that
    an individual, whether privileged or not, gets anequal opportunity to gain profit and ease
    the burden on their shoulders.
**2. Increased cash flow:**

```
Generally, when a bank offers for loan it has a calculatedprofit for the sum and if
migration occurs, as proposed by our app, it willcalculate the sum i.e. (( principal
amount / total time period) x (remaining period))+ (the amount along with the interest
for the locking period). This profit will be lesscompared to the original profit but the
amount they get back can be invested by them in othervolatile assets like stocks,
infrastructures, etc., which will give them moreprofit in the long run thus increasing the
cash flow in the market. A similar phenomenon willhappen when people will migrate
their FD. This will also initiate competition amongthe banks as people will always tend
towards those banks who ask for low rates of interestin loans and provide high rates of
interest in FDs. This will also result in better economicsuggestions to individuals thus
improving living standards.
```

**3. Easy accessibility for senior citizens:**

```
The present methods to open, close, transfer, or evendo any banking function require
hard document presentation or standing in long linesfor people who are not familiar
with online banking and think managing passwords forvarious banks is a hassle. Yes,
the people under consideration are elderly and dependentsections of the society who,
unlike the young and energetic people, need to bedealt with care and often the people in
banking counters are rude to people who are slow tounderstand the process. Though
we can’t blame the workers for their cranky behavioras they have to deal with a lot of
people in a certain time duration, we can providea more warm and cozy platform for
them. Also, rather than managing passwords for variousbanks, they only need to
remember their app password, rest assured our appwill keep the passwords in the
safest way possible.
```
Our model can be used to introduce even other greatbusiness models to open banking that is
right now majorly handled offline or are not availableto the general public which can decrease
the economic adversity to some extent.

### Future scope

```
Few improvements that can be done or features thatcan be added are:-
```
**1. Voice recognition (for differently-abled people )
2. AI-driven financial advice generator
3. Universal Identity storage i.e. passports, voter IDs,etc.
4. A fully functional wallet
5. Better connectivity to healthcare facilities likelife insurances, medical insurances**
    **through AI-generated analysis of decentralized medicalrecords, etc.**



