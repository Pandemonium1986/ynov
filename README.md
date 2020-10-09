| Vms                     | @Ip          |
| :---------------------- | :----------- |
| adjapong-docker-vm      | 85.158.8.79  |
| agnes-docker-vm         | 85.158.8.46  |
| ansible-vm              | 85.158.8.166 |
| ayouni-docker-vm        | 85.158.8.213 |
| azize-docker-vm         | 85.158.8.208 |
| colmant-docker-vm       | 85.158.8.128 |
| diop-docker-vm          | 85.158.8.143 |
| djennane-docker-vm      | 85.158.8.188 |
| dossantos-docker-vm     | 85.158.8.41  |
| egu-docker-vm           | 85.158.8.165 |
| estay-docker-vm         | 85.158.8.2   |
| fonton-docker-vm        | 85.158.8.20  |
| ibriz-docker-vm         | 85.158.8.85  |
| ka-docker-vm            | 85.158.8.129 |
| leib-docker-vm          | 85.158.8.75  |
| leveque-docker-vm       | 85.158.8.89  |
| maitte-docker-vm        | 85.158.8.23  |
| marlier-docker-vm       | 85.158.8.180 |
| martin-docker-vm        | 85.158.8.118 |
| matougui-docker-vm      | 85.158.8.48  |
| ndiaye-docker-vm        | 85.158.8.131 |
| pautasso-docker-vm      | 85.158.8.187 |
| poulier-docker-vm       | 85.158.8.148 |
| rajaratnam-docker-vm    | 85.158.8.150 |
| sackda-docker-vm        | 85.158.8.191 |
| soussan-docker-vm       | 85.158.8.63  |
| tavaressemedo-docker-vm | 85.158.8.11  |
| tedesco-docker-vm       | 85.158.8.107 |
| truong-docker-vm        | 85.158.8.10  |
| tsampikana-docker-vm    | 85.158.8.200 |

sed -i 's/Welcome to nginx!/Welcome to Ynov!/g' index.html

- Installer docker-compose
- Déployer 
   * Nexus
   * Sonar
   * Jenkins
   * Gitea
- Configurer les outils via des variables d'environnements.
- lancer un projet démo : Pandemonium/pic-demo

sed
i '1s/^/daemon off;\n/' /etc/nginx/nginx.conf
