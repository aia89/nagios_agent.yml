# nagios_agent.yml
Nagios is an open source software that can be used for network and infrastructure monitoring. Nagios will monitor servers, switches, applications and services. It alerts the System Administrator when something went wrong and also alerts back when the issues has been rectified.

With Nagios you can:

– Monitor your entire IT infrastructure.
– Identify problems before they occur.
– Know immediately when problems arise.
– Share availability data with stakeholders.hypothetical question
– Detect security breaches.
– Plan and budget for IT upgrades.
– Reduce downtime and business losses.
here is nagios agent configuration yml. you can find roles inside role folder. This yml works for centos 6,7.
---
- hosts: nagios  
  roles:
    - { role: centos6_firewalld, when: ansible_distribution_major_version == '6' }
    - { role: centos7_firewalld, when: ansible_distribution_major_version == '7' }
    - epel_download
    - download_nrpe
    - template_nrpe

  tasks:
    - name: restart NRPE
      service: name=nrpe state=restarted

