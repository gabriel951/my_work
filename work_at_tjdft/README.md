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
had to frequently communicate between themselves. I also added documentation to some of these systems, and a good part of this documentation 
was wrote as **sequence diagrams in PlantUML**. The AI systems were Toth, Maat, Artemis and OdinGPT. 

### Toth 
When a lawyer initiates a lawsuit, he has to point one class and one or more subjects. According to its class and subjects a lawsuit is 
distributed to the corresponding sector in TJDFT. Sometimes lawyers would mistake the correct class and subjects for their lawsuit. 
The consequence was a lot of rework: TJDFT's judicial analyst would have to rectify their mistake, send the lawsuit to the right sector and 
people from the wrong sector would have analysed the lawsuit for nothing.  

Toth was designed to minimize this problem. It is an NLP tool that analyses the lawsuit and suggests the class and the subject.

While in TJDFT my contributions to Toth were: 

1. 

### Maat 
In the Brazilian judicial system we employ "Stay of Proceedings" and "Binding Precedent" to manage mass litigation and ensure jurisprudence 
uniformity. Maat is an AI system that suggests to a TJDFT's judicial analyst when he should apply "Stay of Proceedings" or "Binding Precedent" 
to a process. 

While in TJDFT my contributions to Maat were: 

1. 

### Ártemis 
Different judges have different approaches and for a given lawyer if may be beneficial to have its lawsuit judged by Judge X instead of Judge Y. 
Since a lawsuit is randomly assigned to a Judge, an ill intentioned lawyer may file many equal (or almost equal) lawsuits, hope one is given 
to a favorable Judge and then give up on all the remaining. 

Artemis is an AI system that tries to identify cases like this by analysing lawsuits and seeing the degree of similarity between them. 

While in TJDFT my contributions to Artemis were: 

1. 


### OdinGPT
OdinGPT is an AI system that is being designed with 2 goals in mind. The first goal was set when it was observed that, although most 
lawyers and TJDFT's analysts use a system called PJe to manage lawsuits (filing them, distributing them, ...), the 3 AI systems previously 
mentioned (Toth, Maat, Artemis) were not perfectly integrated in PJe. The second goal is to use LLMs (currently chatGPT) 
to give valuable information to the user about a specific lawsuit X. 

Hence, the idea is that the PJe's user, when searching for lawsuit X, will quickly be redirected 
to OdinGPT's website where he will have all the information coming from Toth/Maat/Artemis and other useful information coming from 
predefined prompts from our LLM (currently chatGPT). 

While in TJDFT my contributions to OdinGPT were: 

1. 


## Work in Data Visualization
Although not my main focus, sometimes I would work on constructing and
maintaining some data dashboards that were important for the TJDFT's law
experts. 

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



### Dashboard on Stay of Prooceedings 
We created a dedicated dashboard to visualize TJDFT's lawsuits currently under "Stay of Proceedings" (*Sobrestamento* in Portuguese) 
or that were under "Stay of Proceedings" in the past. A public version of this dashboard, in Portuguese, is available here. 

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


### Dashboard on e-Carta 
The e-Carta (e-Letter) is a service offered by the Brazilian Post Office (Correios) that functions as a hybrid communication solution (digital +
physical). It is widely used by public entities, especially the Judiciary Branch. There was a dashboard about the use of e-Letters by TJDFT 
written in the ELK Stack. The person that was responsible for mantaining it left the team and since there were no experts in this technology 
we decided that I would redo it using **Power BI**. It was a relatively small task because the **SQL queries** to gather the necessary informations 
did not change. Hence, all I did in this project was: 

1. 



## Other work 
### Article for PTD 
In 2024, the current administration of TJDFT created PTD, the Digital Transformation Program (*Programa de Transformação Digital* in Portuguese) 
to boost the efficiency and quality of Justice, through the improvement of systems and digital services with a user focus. In 2025 they decided to 
publish a book with the results that had been achieved so far. Verônica, Ortegal and I wrote a chapter (in Portuguese) in this book about what 
our team had accomplished since 2024. 

It is available here. 

### Powercenter and ETL 
An old version of Powercenter was the ETL tool used in TJDFT. I learned a tiny fraction of it and helped very briefly with a few
ETL flows while in TJDFT.  

