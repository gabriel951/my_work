# My Work in TJDFT 
Since April of 2023 I am working as a data scientist for the Brazilian government, at TJDFT. 
DF is one of the 27 states in Brazil (and the state of the capital, Brasília) and TJDFT is its judicial court. 
I worked in a relatively small team (most of the time we were 4 employees and 1 intern) that was responsible for some 
internal AI systems (primary) and some data dashboards (secondary). 
Instead of emphasizing specialization, the leadership rotated our participation 
in all the teams's projects to disseminate knowledge to everyone. Hence, I worked a bit on a lot of things during my time there. 


## Work in AI systems 
My work in TJDFT was primary in some internal AI systems. There were 4 of them and in all of them we deployed using a **GitLab CI/CD pipeline**
and **Kubernetes/Openshift** so I acquired a bit of experience with DevOps. These systems all employed the microsservice architecture and 
had to frequently communicate between themselves. Almost all of this microsservices were written in **Python**. 
I also added documentation to some of these systems, and a good part of this documentation 
was wrote as **sequence diagrams in PlantUML**. The AI systems were Toth, Maat, Artemis and OdinGPT. 

<! Se nao aparecer no futuro eu deveria citar que adquiri conhecimentos em RabbitMQ e -> 
<! Colocar que eu sei sobre o Keycloak-> 

### Toth 
When a lawyer initiates a lawsuit, he has to point one class and one or more subjects. According to its class and subjects a lawsuit is 
distributed to the corresponding sector in TJDFT. Sometimes lawyers would mistake the correct class and subjects for their lawsuit. 
The consequence was a lot of rework: TJDFT's judicial analyst would have to rectify their mistake, send the lawsuit to the right sector and 
people from the wrong sector would have analysed the lawsuit for nothing.  

Toth was designed to minimize this problem. It is an NLP tool that analyses the lawsuit and suggests the class and the subject. The final 
decision is still up to the user, Toth only gives a suggestion. 

While in TJDFT my contributions to Toth were: 

1. Helped add the information about the main subject of a lawsuit in the Toth **Postgree Database** which included 
creating this column in the database using **Flyway (Java)** and altering Python code to insert information in this column. 

2. Along with my boss we extended Toth to handle lawsuits in second instance. This involved altering both **Python code** and **Java Spring code** 
since there was a microservice written in Java that made HTTP request to the REST API to obtain information about lawsuit. I also used this task 
as an opportunity to refactor slightly the microsservice that trained the machine learning model.  

### Maat 
In the Brazilian judicial system we employ "Stay of Proceedings" and "Binding Precedent" to manage mass litigation and ensure jurisprudence 
uniformity. Maat is an AI system that suggests to a TJDFT's judicial analyst when he should apply "Stay of Proceedings" or "Binding Precedent" 
to a process. 

We needed specific information from TJDFT's expert (the team was called NUGEPNAC) to put in Maat's **Mongo**
database. Hence we used **Streamlit** to create a website (we called maat-web) to allow them to insert the information we needed. 

While in TJDFT my contributions to Maat were: 

1. Refactored a part of maat-web's code that a colleague had written, to decouple two different services and allow the user to use only one of
them. This involved **Streamlit** (frontend) and **Python, Mongo** (backend).  
2. Improved another page of the website adding a column to the **Streamlit** dashboard. 
3. Created a tab in the website that allowed the user to exclude information from our **Mongo** database. Used **Keycloak** to handle 
authentication/authorization since not every user of the website was allowed to use this feature. 
4. Created a tab in the website that showed a list of lawsuits and allowed the user to fill/edit information (in a form) about them and register 
in the database. Hence, the technologies involved were **Streamlit**, **Python** and **Mongo**.  


### Ártemis 
Different judges have different approaches and for a given lawyer if may be beneficial to have its lawsuit judged by Judge X instead of Judge Y. 
Since a lawsuit is randomly assigned to a Judge, an ill intentioned lawyer may file many equal (or almost equal) lawsuits, hope one is given 
to a favorable Judge and then give up on all the remaining. 

Artemis is an AI system that tries to identify cases like this by analysing lawsuits and seeing the degree of similarity between them. 

While in TJDFT my contributions to Artemis were: 

1. Added a field to Artemis' **Mongo database** main collection about lawsuits. 
2. Added users, allowing them to access the system. 
3. Added a new functionality that allows the Artemis user to import lawsuits and related ones (ones where the litigants/lawyer was the same) 
to the Artemis database. In addition to 
**Python** code this involved altering the frontend (using **Javascript, NodeJS, Bootstrap** and **Chrome Dev Tools** when things went wrong), 
communicating with other microservices (using **RabbitMQ**), consulting and saving information in the database (using **Oracle SQL** and **Mongo**) 
and deploying the new microsservice to **Openshift 3**. 
4. Implemented logging in the frontend of Ártemis. Used this as an opportunity to simplify and standardize the structure of the system 
(main commit had 547 insertions and 6175 deletions). Implementing the logger involved **Javascript/NodeJS** and **Pino**. When deploying fixed a 
bug in the desenv environment that involved using **Helm/Openshift 4** to increase the timeout in a route. I also documented the website with a 
simple `README.md` and documented the 5 different ways the frontend could communicate with the backend via **PlantUML sequence diagrams**. 




### OdinGPT
OdinGPT is an AI system that is being designed with 2 goals in mind. The first goal was set when it was observed that, although most 
lawyers and TJDFT's analysts use a system called PJe to manage lawsuits (filing them, distributing them, ...), the 3 AI systems previously 
mentioned (Toth, Maat, Artemis) were not perfectly integrated in PJe. The second goal is to use LLMs (currently chatGPT) 
to give valuable information to the user about a specific lawsuit X. 

Hence, the idea is that the PJe's user, when searching for lawsuit X, will quickly be redirected 
to OdinGPT's website where he will have all the information coming from Toth/Maat/Artemis and other useful information coming from 
predefined prompts from our LLM (currently chatGPT). 

While in TJDFT my contributions to OdinGPT were: 

1. We wanted to extract the mention to regulations inside a lawsuit. I decided and implemented a **regular expression** that successfully 
identified the regulations in a lawsuit. 
2. Used **Python** to make HTTP requests to a REST API that contained useful data.  
3. We wanted the user to rate how well OdinGPT was giving the information about lawsuits. I implemented a ranking functionality in Odin's 
website (written in **Streamlit**) that allowed the user to rate OdinGPT's performance. 
4. Fixed bug regarding the use of cookies in Odin's website. 
5. This project gave me more experience in Keycloak: I extended **KeyCloak**'s token expiration time and also added users from our team 
to adequate roles in **KeyCloak**'s client. 
6. Consumed a **GraphQL** API to obtain information about the user (gender/role) which we used to customize the greetings' message in Odin. 
7. Configured **PowerAutomate** to send messages notifying users about important events in Microsoft Teams. 



## Work in Data Visualization
Although not my main focus, sometimes I would work on constructing and
maintaining some data dashboards that were important for the TJDFT's law
experts. 

### Dashboard on Stay of Prooceedings 
We created a dedicated dashboard to visualize TJDFT's lawsuits currently under "Stay of Proceedings" (*Sobrestamento* in Portuguese) 
or that were under "Stay of Proceedings" in the past. A public version of this dashboard, in Portuguese, is available [here](https://app.powerbi.com/view?r=eyJrIjoiYzg0NjdjZTMtZDQ2YS00MDZlLTk4NGMtZGRlZTM1MDM1NTgyIiwidCI6ImRjNDIwMDkyLTIyNDctNDMzMC04ZjE1LWY5ZDEzZWViZWRhNCJ9). 

We used **Power BI** to construct a dashboard showing the total number of
lawsuits currently under "Stay of Proceedings" or that were under "Stay of
Proceedings". It also has a graph showing the amount per year and a table
showing every lawsuit along with its instance;
judging sector; Judges'Chambers/Special Courts/Trial Courts; theme; type; date
the lawsuit was put under "stay of proceedings"; distribution date; date (if
any) the lawsuit was taken out of "stay of proceedings"; date of judgement (if
any); and archiving date (if any). As expected the 
dashboard had filters, allowing the user to see only lawsuits: "stay of
proceedings" year and month; instance; type; theme; Judges'Chambers/Special
Courts/Trial Courts; Judging Sector; if it has/has not beeing archived; if it
has/has not being judged; and if it is/is not currently under "stay of
proceedings". 

While in TJDFT my contributions to this dashboard were: 
1. Constructed, along a coworker, **Oracle SQL queries** that grouped information together in **materialized views** that were accessed 
by the dashboard. Suggested the use of **Common Table Expressions** to my team to make the queries cleaner, 
a concept the team was not familiar with.
2. Along with a coworker, constructed the dashboard. 
3. Mantained the dashboard for more than 2 years, adding information such as "Judges'Chambers/Special Courts/Trial Courts". 
I also constructed an extended restricted dashboard that contained additional information about "weakly classified" lawsuits. 
The dashboard required a **Power BI license** and would be used by approximately 10 people from a team called NUGEPNAC. 
However we did not have that many licenses available so I also constructed a **Python program** that took the main information in 
this dashboard and uploaded it as  `.csv` files in a One-Drive folder shared with NUGEPNAC. 
4. The dashboard also showed some information mismatch with some internal reports, which I investigated and mapped 
using **Jupyter Notebooks**. There were some small methodological differences between the two that explain the differences.


### Dashboard of Class Actions 
Class actions are a critical component of the legal system, especially in civil
law, because they provide a mechanism for large groups of people—who have
suffered the same harm—to seek justice collectively. We constructed a dashboard to show relevant information about it. 

We used **Qlik Sense Desktop** to construct a dashboard showing strategic information about the number of class actions handled by TJDFT, dividing by: 
whether this actions are being handled or were already handled; the amount per year; the amount per subject and per class. The dashboard 
also contained more detailed data in the format of table with the list of each class action along with its instance, class, distribution date, 
judging sector, description of the last update, date of last update, value of claim, main subject and judgement date 
(if there was already a judgement). As expected the dashboard had filters, allowing the user to see only lawsuits from certain 
instance, judging sector, assigned judge, class, judgement year, or the description of the last update. 

While in TJDFT my contributions to this dashboards were: 

1. Helped a coworker construct the **Oracle SQL queries** that grouped information together in materialized views that were accessed 
by the dashboard. Suggested the use of **Common Table Expressions** to my team to make the queries cleaner, 
a concept the team was not familiar with. 

2. Helped the coworker construct **Oracle's Stored Procedures** to update the materialized views daily. 

2. Constructed the dashboard under the supervision of another coworker. 




### Dashboard on e-Carta 
The e-Carta (e-Letter) is a service offered by the Brazilian Post Office (Correios) that functions as a hybrid communication solution (digital +
physical). It is widely used by public entities, especially the Judiciary Branch. There was a dashboard about the use of e-Letters by TJDFT 
written in the ELK Stack. The person that was responsible for mantaining it left the team and since there were no experts in this technology 
we decided that I would redo it using **Power BI**. It was a relatively small task because the **SQL queries** to gather the necessary informations 
did not change. Hence, all I did in this project was: 

1. Did some exploratory data analysis in **Jupyter** to understand the data returned by our **SQL queries**. 
2. Constructed a **PowerBi Dashboard** mirroring a previous dashboard we had in the ELK stack. 



## Other work 
### DMJud 
TJDFT and other courts in Brazil are supervised by CNJ (National Council of Justice). CNJ computes a set of metrics that it uses to 
rank courts and award prizes to top courts. This is taken very seriously in TJDFT with everyone wanting to finish the year in the top spots. 
CNJ computes this metrics/statistics according to some reasonable intricate business rules and updates them sparingly (sometimes once a month). 
The project called DMJud computes (for TJDFT) the same metrics/statistics than CNJ but updates them much quicker (our aim is D-1). It uses 
**Java Spring** and queries our **Oracle SQL database**. 

While in TJDFT my contributions to this project were: 
1. Along with 2 more colleagues, we helped the main developer by writting some **unit tests in Java**. 


### Article for PTD 
In 2024, the current administration of TJDFT created PTD, the Digital Transformation Program (*Programa de Transformação Digital* in Portuguese) 
to boost the efficiency and quality of Justice, through the improvement of systems and digital services with a user focus. In 2025 they decided to 
publish a book with the results that had been achieved so far. Verônica, Ortegal and I wrote a chapter (in Portuguese) in this book about what 
our team had accomplished since 2024. 

It is available here. 

### Powercenter and ETL 
An old version of Powercenter was the ETL tool used in TJDFT. I learned a tiny fraction of it and helped very briefly with a few
ETL flows while in TJDFT.  

### Stackoverflow for teams
I pushed for my organization to adopt (the free version of) Stackoverflow for teams. When I left the platform had more than 
70 posts, most of them with answers. The results were mixed. One one hand it was useful in when different colleagues asked the same question 
and also when a new employee entered our team. On the other hand I was the only one who posted questions/answers. 

### Monitoring Codex
Codex was a project that was experiencing some downtime. I helped a colleague implement a Python program that periodically checked whether 
the service was on and if it was not then it send **notifications in Teams (via Power Automate), Telegram and email**. 

