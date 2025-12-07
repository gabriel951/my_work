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
When a lawyer initiates a petition, he has to point one class and one or more subjects. According to its class and subjects a petition is 
distributed to the corresponding sector in TJDFT. Sometimes lawyers would mistake the correct class and subjects for their petition. 
The consequence was a lot of rework: TJDFT's judicial analyst would have to rectify their mistake, send the petition to the right sector and 
people from the wrong sector would have analysed the petition for nothing.  

Toth was designed to minimize this problem. It is an NLP tool that analyses the petition and suggests the class and the subject.

While in TJDFT here were my contributions to Toth: 

1. 

### Maat 
In the Brazilian judicial system we employ "Stay of Proceedings" and "Binding Precedent" to manage mass litigation and ensure jurisprudence 
uniformity. Maat is an AI system that suggests to a TJDFT's judicial analyst when he should apply "Stay of Proceedings" or "Binding Precedent" 
to a process. 

While in TJDFT my contributions to Maat were: 

### Artemis 
Different judges have different approaches and for a given lawyer if may be beneficial to have its lawsuit judged by Judge X instead of Judge Y. 
Since a process is randomly assigned to a Judge, an ill intentioned lawyer may file many equal (or almost equal) lawsuits 



### OdinGPT



## Work in Data Visualization

## TODO: paper 
