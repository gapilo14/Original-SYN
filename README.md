# Implementation of "Original SYN: Finding machines hidden behind firewalls"
This repository contains an implementation of the ["Original SYN: Finding machines hidden behind firewalls"](https://ieeexplore.ieee.org/document/7218441) paper published in IEEE in 2015. Among the multiple objectives, we wanted to understand if the attack type proposed in the paper is still valid in 2024 and, if so, what limitations (or fixes) are introduced by the new versions of the Linux kernel. 

### Code
The implementation is in Python, while the custom sockets are written in C; we suggest customising the parameters according to your network topology and hardware resources.

### Network topologies
The first two topologies (not useful for the final implementation but an important part of the conducted experiment) and the test topology (useful for debugging) are based on Docker containers. The final topology, on the other hand, is composed of virtual machines which require manual setup in the preferred virtualisation environment; in `Networks/Third-topology`, a small guide is available for recreating our network topology using Proxmox. 

### Further informations
For all the information, objectives, discoveries and experiments, please refer to `Report.pdf`.

The project was realised as part of the course "[Network Security](https://www.unive.it/data/insegnamento/398300)" of the [Master Degree in Computer Science and Information Technology](https://www.unive.it/web/en/7056/home) at [Ca' Foscari University of Venice](https://www.unive.it/) with the supervision of Professor [Leonardo Maccari](https://www.unive.it/data/persone/21550550).

### Contacts
For further information please feel free to email the authors: <br>
[Elisa Rizzo](mailto:884784@stud.unive.it) <br>
[Gabriele Pilotto](mailto:902388@stud.unive.it) <br>
[Marco Chinellato](mailto:886217@stud.unive.it) <br>
[Martino Pistellato](mailto:886493@stud.unive.it) <br>
[Thomas Vego Scocco](mailto:884984@stud.unive.it)
