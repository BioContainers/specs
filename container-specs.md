Container Specifications
========================

Each container should provide a well-defined metadata header that allows the final users to test, deploy and get support around the container.
We explain here the containers metadata, their meaning and use in BioContainers:



| Field                 | Description                                                                                                                | Example                                                  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| base_image            | The original image where the software has been built                                                                       | base image: biodckr/biodocker                            |
| software_version      | Every BioContainer should contain the actual version of the software and tool                                               | software version: 2015020                                |
| software              | Name of the software                                                                                                       | software: Comet                                          |
| description           | A short description of the software or tool.                                                                               | description: Peptide identification search tool          |
| home                  | The original software website where the user can find information about the tool the algorithms and examples.               | website: http://comet-ms.sourceforge.net/                |
| documentation         | URL(s) containing information about how to use the software.                                                               | doc pages: http://comet-ms.sourceforge.net/              |
| license               | SPDX license specification. If not in the SPDX list, then set short description and specify URL in license_file>                                                                                   | SPDX:Apache-2.0          |
| license_file          | license path location in the container or url (according to license requirements |          |  
| tags                  | Tags about the software that enable to find and classify the software tool.                                                 | tags: proteomics, mass spectrometry, biocontainers       |


### Dockerfile example:

~~~
# Base Image
FROM biocontainers/biocontainers:latest

# Metadata
LABEL base.image="biocontainers:latest"
LABEL version="3"
LABEL software="Comet"
LABEL software_version="2016012"
LABEL description="an open source tandem mass spectrometry sequence database search tool"
LABEL home="http://comet-ms.sourceforge.net/"
LABEL documentation="http://comet-ms.sourceforge.net/parameters/parameters_2016010/"
LABEL license="SPDX:Apache-2.0"
LABEL license_file="/usr/share/common-licenses/Apache-2.0"
LABEL tags="Proteomics"

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

CMD ["comet"]
~~~
