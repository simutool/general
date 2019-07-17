This is the entry point to the SIMUTOOL Knowledge Management Suite (KMS) of software published under the [simutool github organization](https://github.com/simutool).

## In a nutshell

- This is a data management tool. 
- Intended to be useful on an *organization-wide scale* and a cross-organizational setting.
- The origanization-wide data management problem is also a Knowledge Management problem.
- Its primitives are a (1) *dataset* (a logical unit of data) and (2) *document* (file, unstructured blob).

- **We add a semantic layer describing all these data primitives.**
- **We embedd these descriptions within the larger organizational 'knowledge base' (which is in turn a description of all the notable activities, agents, resources out there).**

- It is a work in progress (meaning its vision has not been completely implemented yet).
- This work views the p
 

The goal of the KMS is to do data-centric knowledge management. knowledge management


![Conmponents](components.png)

## The Science

The goal of this project is to propose a system design for *facilitating knowledge transfer across the different activities of digital manufacturing* and other similar domains. The work is divided into two parts: a  **(meta)data model** and a **Knowledge Management process**.

*  **The (Metadata) Model**: *A thin semantic graph model + a domain model that drives various parts of the system*. We start with a basic (property) graph database model; nodes with simple properties and named relations across nodes. We then develop a software component to create a thin semantic layer of types and subtypes, and controlled vocabularies to our original model. Since we built it we add other minor functionalities to model that we see as useful. We also develop a domain model to go along with the system.
*  **The Process**: A system design for the *capture*, *creation*, *sharing*, *dissemination*, *acquiring*, and *application* of (meta)data in the above model.

Its motivating domain was that of [digital manufacturing](https://cordis.europa.eu/project/rcn/198371), where many types of digital resources (sensor data, simulation data, CAD/CAM etc.) and information about them is being produced and consumed on a day to day basis. But we have done our best to make it generic enough to work on [other](https://www.uni-bamberg.de/en/mobi/research/futureiot/), [domains](https://www.uni-bamberg.de/mobi/forschung/living-lab-bamberg/informationen-zur-datenerhebung/).


# Knowledge  Graph Service and its Web Application

Central unit of the SKM Platform, this project contains two modules:

* The *Knowledge Graph Service (kgservice), and its API interface*: Which is the semantic metadata store at the heart of the SKM Platform.
* The *Web Application* for administration and web access to the contents of the Knowledge Graph. 
* The File server.


## How to install (Debian)

Get web2py source and clone this repo

```shell
foo@bar:~$ mkdir /home/www-data
foo@bar:~$ cd /home/www-data
foo@bar:~$ wget https://mdipierro.pythonanywhere.com/examples/static/web2py_src.zip
foo@bar:~$ unzip web2py_src.zip
foo@bar:~$ rm web2py_src.zip
foo@bar:~$ cd web2py/applications
foo@bar:~$ git clone https://...../simutool/simutool_kms.git
foo@bar:~$ cp simutool_kms/private/appconfig.ini_template  simutool_kms/private/appconfig.ini 
```

Install pip and the required libraries

```shell
foo@bar:~$ apt-get install python-pip -y
foo@bar:~$ python -m pip install --upgrade pip
foo@bar:~$ cd /home/www-data/web2py/applications/simutool_kms
foo@bar:~$ pip install -r requirements.txt
```

Run web2py

```shell
foo@bar:~$ cd /home/www-data/web2py/
foo@bar:~$ python web2py.py --password="[select_a_password]"
```

You can access the the application at http://127.0.0.1:8000/simutool_kms/default/index

The first user login credentials (admin) can be found in `/home/www-data/web2py/applications/simutool_kms/private/appconfig.ini` under `admin_email = XXXX`, `admin_pass = YYYYYY`


## Project Background

This project serves as the core of the Knolwedge Management System designed and developed for the [SIMUTOOL EC Project](https://cordis.europa.eu/project/rcn/198371). It was developed by the [Chair of Mobile Software Systems (MOBI)](https://www.uni-bamberg.de/en/mobi/) in the [University of Bamberg](https://www.uni-bamberg.de). 

This project is the result of the labour of many people under a common goal:

* Daniela Nicklas - *Lead*
* Nasr Kasrin - *Product Owner | Software Architecture*
* Adrian Lengenfelder - *Development | Devops*
* Maliha Qureshi - *Product owner of the first iteration of the semantic web side of the Project*
* Simon Steuer - *Product owner of the first iteration of the Online Monitoring Tool*
* Valentyna Voronova - *Development*
* Lukas Genßler - *Development*
* Katharina Broswik - *Web UI Development | Usability*
* Harshit Gupta - *Development on an early prototype of the Automated File Uploader and others*
