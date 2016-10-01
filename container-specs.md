Container Specifications
========================

Each container should provide a well-defined metadata that allows the final users to test, deploy and get support around the container. 
We explain here the containers metadata, their meaning and use in BioContainers: 
 


| Field                 | Description                                                                                                                | Example                                                  | 
|-----------------------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| software version      | Every Biocontainer should contains the actual version of the software and tool                                             | software version: 2015020                                | 
| software              | Name of the software                                                                                                       | software: Comet                                          |
| description           | A short description of the software or tool.                                                                               | description: Peptide identification search tool          | 
| website               | The original software website where the user can find information about the tool the algorithms and examples.              | website: http://comet-ms.sourceforge.net/                | 
| tags                  | Tags about the software that enable to find and classify the software tool.                                                | tags: proteomics, mass spectrometry, biocontainers       |                   
| base image            | The original image where the software has been built                                                                       | base image: biodckr/biodocker                            |
| run cmd               | Example on how to execute the given container                                                                              | run cmd: docker run biodckr/comet <options> <files>      | 
| maintainer            | The information about the maintainer of the software and the tool                                                          | maintainer: Yasset Pere-Riverol <yperez@ebi.ac.uk>       |
| help page             | This property and attribute contains provides help page information about the tool                                         | help pages: http://comet-ms.sourceforge.net/             | 
  
  
### DockerFile container example: 



