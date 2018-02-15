Container Specifications
========================

Each container should provide a well-defined metadata header that allows the final users to test, deploy and get support around the container.
We explain here the containers metadata, their meaning and use in BioContainers:



| Field                 | Description                                                                                                                | Example                                                  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| base_image            | The original image where the software has been built | base_image: biodckr/biodocker |
| software.version      | Version of the software and tool                     | software.version: 2015020     |
| software              | Name of the software                                 | software: Comet               |
| about.summary         | A short description of the software or tool.         | about.summary: Peptide identification|
| about.home            | The original software website where  and examples.   | about.home: http://comet-ms.sourceforge.net/  |
| about.documentation   | URL(s) containing information about software            | about.documentation: http://comet-ms.sourceforge.net/     |
| about.license         | SPDX license specification. If not in the SPDX list, then set short description and specify URL in license_file>           | about.license: SPDX:Apache-2.0          |
| about.license_file    | license path location in the container or url (according to license requirements |          |  
| about.tags            | Tags about the software that enable to find and classify the software tool.| about.tags: proteomics, mass spectrometry, biocontainers       |


### Dockerfile example:

~~~
# Base Image
FROM biocontainers/biocontainers:latest

# Metadata
LABEL base_image="biocontainers:latest"
LABEL version="3"
LABEL software="Comet"
LABEL software.version="2016012"
LABEL about.summary="an open source tandem mass spectrometry sequence database search tool"
LABEL about.home="http://comet-ms.sourceforge.net/"
LABEL about.documentation="http://comet-ms.sourceforge.net/parameters/parameters_2016010/"
LABEL about.license="SPDX:Apache-2.0"
LABEL about.license_file="/usr/share/common-licenses/Apache-2.0"
LABEL about.tags="Proteomics"

# Maintainer
MAINTAINER Felipe da Veiga Leprevost <felipe@leprevost.com.br>

USER biodocker

RUN ZIP=comet_binaries_2016012.zip && \
  wget https://github.com/BioDocker/software-archive/releases/download/Comet/$ZIP -O /tmp/$ZIP && \
  unzip /tmp/$ZIP -d /home/biodocker/bin/Comet/ && \
  chmod -R 755 /home/biodocker/bin/Comet/* && \
  rm /tmp/$ZIP

RUN mv /home/biodocker/bin/Comet/comet_binaries_2016012/comet.2016012.linux.exe /home/biodocker/bin/Comet/comet

ENV PATH /home/biodocker/bin/Comet:$PATH

WORKDIR /data/

~~~
