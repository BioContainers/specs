Container Specifications
========================

Each container should provide a well-defined metadata header that allows the final users to test, deploy and get support around the container.
We explain here the containers metadata, their meaning and use in BioContainers:



| Field                 | Description                                                                                                                | Example                                                  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| base image            | The original image where the software has been built                                                                       | base image: biodckr/biodocker                            |
| version      | Every BioContainer should contain the actual version of the software and tool                                              | software version: 2015020                                |
| name              | Name of the software                                                                                                       | org.label-schema.name: Comet                                          |
| description           | A short description of the software or tool.                                                                               | description: Peptide identification search tool          |
| url               | The original software website where the user can find information about the tool the algorithms and examples.              | url: http://comet-ms.sourceforge.net/                |
| documentation         | URL(s) containing information about how to use the software.                                                               | doc pages: http://comet-ms.sourceforge.net/              |
| license               | URL(s) containing Licensing information.                                                                                   | license page: http://comet-ms.sourceforge.net/           |  
| tags                  | Tags about the software that enable to find and classify the software tool.                                                | tags: proteomics, mass spectrometry, biocontainers       |


### Dockerfile example:

~~~
# Base Image
FROM biocontainers/biocontainers:latest

# Metadata

# label-schema.org common metadata fields
LABEL org.label-schema.schema-version = "1.0"  # We are using version 1.0 of the Label schema http://label-schema.org/rc1/
LABEL org.label-schema.name="Comet"
LABEL org.label-schema.version="2016012"
LABEL org.label-schema.description="an open source tandem mass spectrometry sequence database search tool"
LABEL org.label-schema.url="http://comet-ms.sourceforge.net/"
LABEL org.label-schema.vendor="biocontainers.pro"

# biocontainers specific metadata fields
LABEL pro.biocontainers.base-image="biocontainers:latest"
LABEL pro.biocontainers.documentation="http://comet-ms.sourceforge.net/parameters/parameters_2016010/"
LABEL pro.biocontainers.license="http://comet-ms.sourceforge.net/"
LABEL pro.biocontainers.tags="Proteomics"

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
