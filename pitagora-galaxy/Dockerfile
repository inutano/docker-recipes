# Pitagora Galaxy
#
# VERSION       0.1

FROM bgruening/galaxy-stable:latest_2014.08.11

MAINTAINER Tazro Inutano Ohta, inutano@gmail.com

RUN sed -i 's|brand.*|brand = pitagoraGalaxy|g' ~/galaxy-central/universe_wsgi.ini

WORKDIR /galaxy-central
ADD ./install_repo_wrapper.sh /galaxy-central/install_repo_wrapper.sh
RUN chmod +x ./install_repo_wrapper.sh

# Install BWA, FastQC, Tophat2, Cufflinks, SAM-to-BAM, MACS2
RUN ./install_repo_wrapper.sh \
    "--url http://toolshed.g2.bx.psu.edu/ -o devteam --name bwa_wrappers --panel-section-id pitagora_tools"
RUN ./install_repo_wrapper.sh \
    "--url http://toolshed.g2.bx.psu.edu/ -o devteam --name fastqc --panel-section-id pitagora_tools"
RUN ./install_repo_wrapper.sh \
    "--url http://toolshed.g2.bx.psu.edu/ -o devteam --name tophat2 --panel-section-id pitagora_tools"
RUN ./install_repo_wrapper.sh \
    "--url http://toolshed.g2.bx.psu.edu/ -o devteam --name cufflinks --panel-section-id pitagora_tools"
RUN ./install_repo_wrapper.sh \
    "--url http://toolshed.g2.bx.psu.edu/ -o devteam --name sam_to_bam --panel-section-id pitagora_tools"
RUN ./install_repo_wrapper.sh \
    "--url http://toolshed.g2.bx.psu.edu/ -o modencode-dcc --name macs2 --panel-section-id pitagora_tools"

# Mark one folders as imported from the host.
VOLUME ["/export/"]

# Expose port 80 to the host
EXPOSE :80

# Autostart script that is invoked during container start
CMD ["/usr/bin/startup"]
