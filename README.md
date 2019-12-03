API startup steps

List of all APIs with their host name as below:

Experience API:
http://experience-contactmanagement-db-api.us-e2.cloudhub.io/

Process API:
http://contactmanagement-process-db-api.us-e2.cloudhub.io/

System API:
http://system-contact-db-api.us-e2.cloudhub.io/
http://system-address-db-api.us-e2.cloudhub.io/
http://system-communication-db-api.us-e2.cloudhub.io/

resource names and required parameters to call the API, can be found in respective API’s RAML file.



Post deployment of APIs need to provide below environment variables for all APIs:
mule.env=dev
For system APIs along with environment names (using above property) need to provide below key as well for database password decryption
secret.key=demo


![dbTableStructure](https://github.com/sneha-github/experience-contactmanagement-db-api/blob/master/dbTableStructure.jpeg)

Database Table Creation Script

CREATE TABLE dbo.contacts (
    contactID int NOT NULL IDENTITY(1,1),
    firstName varchar(50) NULL,
    lastName varchar(50) NULL,
    dob varchar(50) NULL,
    gender varchar(50) NULL,
    title varchar(50) NULL,
    email varchar(50) NOT NULL
);
ALTER TABLE dbo.contacts ADD CONSTRAINT PK__contacts__7121FD151C9E6867 PRIMARY KEY (contactID);

CREATETABLEdbo.contactAddress (
	idintNOTNULLIDENTITY(1,1),
	contactIdintNOTNULL,
	[type] varchar(50) NULL,
	numbervarchar(50) NULL,
	streetvarchar(50) NULL,
	unitvarchar(50) NULL,
	cityvarchar(50) NULL,
	statevarchar(50) NULL,
	zipcodevarchar(50) NULL
);
ALTERTABLEdbo.contactAddressADDCONSTRAINT PK__contactA__3213E83F5513B6D5 PRIMARYKEY (id);

CREATE TABLE dbo.contactCommunication (
    id int NOT NULL IDENTITY(1,1),
    contactId int NOT NULL,
    [type] varchar(50) NULL,
    value varchar(50) NULL,
    preffered varchar(50) NULL
);
ALTER TABLE dbo.contactCommunication ADD CONSTRAINT PK__contactC__3213E83FCAA30ADA PRIMARY KEY (id);
