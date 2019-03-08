# Git Workflows

Contenido:

* Single Flow
* GitHub Workflow
* Feature Branch
* Git flow

---

### Single Flow

Este flujo de trabajo con git es muy útil cuando se trabaja individualmente, consta de un sólo branch.![](/assets/wf1.png)

### GitHub Workflow 

Este flujo de trabajo considera en crear un branch para agregar n cambios y gestionarlos mediante GitHub.

1. Se crea un branch
2. Se agregan los cambios
3. Se actualiza el repositorio remoto de GitHub
4. Se abre un Pull Request 
5. Se efectúa un code review
6. Se mezclan los cambios
7. Despliegue 

### Abrir pull request![](/assets/gw2.png)

La pestaña de Pull Request tendrá los PR realizados![](/assets/gw3.png)Ahi mismo se podrá mezclar el PR ![](/assets/gw4.png)  


### Feature Branch

Esta es una forma de trabajar con git basada en desarrollar features, para ello la mayoría de las plataformas de repositorios remotos tienen la misma funcionalidad implementada.

1. Identificar los issues a crear 
2. Asignarles un identificador por issue mediante la plataforma. Cada issue será un branch.
3. Identificar los ambientes de desarrollo que se considerarán como branches independientes: desarrollo\(master\), QA, STAGE, UAT, PROD.
4. Cada uno de estos branch se desplegará por separado. 
5. Cada branch correspondiente a un issue se mezclará a cada branch correspondiente a los ambientes.

Asignación de issues![](/assets/gw8.png)![](/assets/gw9.png)Ejemplo del log de un proyecto versionado con feature-branch:

```
* 710d6b0  hace 3 meses carlogilmar  #38 Modify medical records endpoint
* be7725a  hace 4 meses Jorge Acosta Lemus #17 Adding wkhtmltopdf binary and modify jenkinfile to add binary to container
* 41cc24c  hace 4 meses carlogilmar #22 Adding styles in the email body
* 05c33b7  hace 4 meses carlogilmar #16 Implement emails and missing endpoints
* 1c4ecd0  hace 4 meses carlogilmar #19 Implement security auth in pdf generator endpoint
* 9445f2c  hace 4 meses carlogilmar  #21 Create a second endpoint for the new pdf
* bf731c4  hace 4 meses carlogilmar  #20 Create endpoint for generate pdf
* 91a4316  hace 4 meses carlogilmar #18 tore the pdf information as medical record and create endpoints for save and get by email
* cbf9978  (origin/feature/15, master-bk, feature/15) hace 4 meses carlogilmar  #15 Connect endpoint medical record to generate a pdf
* 7ec6c47  (origin/feature/14, feature/14) hace 4 meses carlogilmar  #14 Create the sanofi pdf format
* a4e46e8  hace 4 meses carlogilmar  #11 Add endpoint for get the medical record id
* 305a454  hace 4 meses carlogilmar  #12 Adding email notification when activate an user
* 483a13f  (origin/feature/13, feature/13) hace 4 meses carlogilmar  #13 Create a pdf
* 7ada7f2  (origin/feature/7, feature/12) hace 4 meses carlogilmar  #7 Adding config for deploy webapp in qa environment
* 769a88b  hace 4 meses carlogilmar  #6 Create validation view
* 1e66e76  (origin/feature/5, feature/5) hace 4 meses carlogilmar  #5 Implement sanofi assets
* 55e57ad  hace 4 meses carlogilmar  #4 Adding login with guardian for the web app
* 1369751  hace 4 meses carlogilmar  #3 Adding views to the phoenix project
* 5ce232f  hace 4 meses carlogilmar  #2 Adding endpoint for validate a user
* 742d97f  hace 5 meses carlogilmar  #1 Adding deploy config
```

### TODO: Git Flow



