# Projet élément finis #

**J'AI REPRIS LE README DU PROJET 3 (threads en c) QU'IL FAUDRA MODIFIER POUR CE PROJET CI**



## Le projet
TESTCAMmm
Notre programme est une implémentation d'une problème d'élasticité linéaire plane en language C. L'objectif est de trouver le plus court chemin ayant le plus grand coût, d'un noeuds source à un noeuds destination d'un graphe orienté et pondéré pouvant contenir des poids négatifs.



## Le code

    # Spécifications:
    Notre code prend un fichier binaire, qui représente un graphe, en entrée et retourne un fichier binaire représentant:
    - le nombre de noeuds du graphe
    - un ensemble avec: - le noeud source,
                        - le noeud de destination, 
                        - le coût de ce plus court chemin et le nombre de noeuds que traverse ce plus court chemin.
    
    # Structure du code:
    Tout d'abord, nous lisons à l'aide de la fonction "read_graph" le fichier binaire d'entrée en extrayant les informations du graphe (nombre de noeuds, nombre d'arêtes et les couts).
    Ensuite, dans la fonction "bellman_ford nous implémentons l'algorithme de Bellman Ford sur ce graphe. Cette fonction nous renvoie une structure reprenant la distance et le chemin suivi.
    Par la suite, nous executons la fonction "get_max" afin de pouvoir avoir une structure reprenant le coût maximal de notre chemin avec l'indice du noeud atteignable depuis la source. 
    Nous exécutons ensuite la fonction "get_path" qui permet d'obtenir une liste reprenant le chemin pour aller de la source à la destination.
    Finalement, nous traduisons ces informations en un fichier binaire que nous retournons.

    # Structure des dossiers:
    Les programmes principaux tels que "sp.py" et "sp.c" se trouvent dans le dossier principale du projet, qui contient donc l'entièreté du projet.
    Les autres progammes sont classés dans les dossiers "include", "src" et "tests". 
    Dans le dossier "include" se trouvent tous les fichiers headers contenant la déclaration de chacune des fonctions que nous utiliserons. Ce seront ces fichiers que nous inclurons dans nos programmes afin d'utiliser les méthodes implémentées. 
    Dans le dossier "src" se trouvent les codes sources de chacune de nos méthodes.
    Dans le dossier "tests" se trouvent tous les codes sources des tests que nous avons implémentés, ainsi que le fichier "test_suite" qui nous permettra d'exécuter les tests. 



## Compilation
Informations sur comment compiler le code via le terminal

Notre Makefile contient les commandes (automatisées) suivantes:

    * make sp :
    Cette commande compile tout le code. 
    Un exécutable, nommé "sp", est alors généré.
    Pour éxécuter le programme, utilisez la ligne suivante sur le terminal: 
    ./sp [-f "outputFile"] [-v] [-n] "inputFile"
        # Arguments:
        (les arguments entre crochets sont optionnels)
            * -f "outputFile" : le nom du fichier binaire de sortie dans lequel les résultats vont être écrits (=stoud par défault)
            * -v : permet l'affichage de messages de débogage
            * -n : idique le nombre de threads utilisés (=1 par défault)
            * "inputFile" : le nom du fichier binaire d'entrée (peut être créé par make graph)
    
    Par exemple, vous pouvez faire : ./sp -f output.bin -v graph.bin

    * make graph :
    Cette commande permet de créer un graphe d'entrée pour pouvoir exécuter notre programme. Elle créera automatiquement un graphe avec un nombre de noeuds et de liens aléatoire et variable d'une fois à l'autre.
    Pour créer un graphe personnalisé, il suffit d'entrer dans le terminal la commande:
    python3 create_graph.py -o "nomdufichier.bin" -n [x] -l [y]  
        # Arguments:
            * "nomDuFichier.bin" représente le nom du fichier contenant le graphe nouvellement créé
            * x est le nombre de noeuds
            * y est le nombre de lien
    
    * make exec_python
    Cette commande permet d'exécuter le programme python "sp.py" avec un fichier d'entrée "graph.bin".
    (nécessite d'avoir exécuté la commande make graph au préalable)

    * make test :
    Cette commande permet de compiler les tests et de les exécuter.
    
    Avant d'utiliser cette commande, il faut utiliser "make graph" permettant de créer le fichier d'entrée des programmes "sp.c" et "sp.py". Ensuite , il faut utiliser "make sp", puis "./sp graph.bin -f output_c.bin" (pour que la comparaison des fichiers de sortie python et C puissent être comparés), ce qui permet de compiler le code en C, afin de compiler les fonctions que nous testons et qui sont donc appelées dans nos tests. Pour finir, on fait la commande "make exec_python" qui exécutera le code python et aura comme fichier de sortie "output_py.bin", qui sera utile pour une des fonctions tests.
    
    Pour exécuter les fichiers tests, il faut exécuter la commande "make test", puis "./test"


    * make clean : 
    Cette commande supprime les fichiers exécutables.



## Les tests
    
    # Tests indépendants: (avec CUnit)
    Nous avons plusieurs tests différents, propres aux fonctions principales de notre programme, afin de vérifier leurs bon fonctionnement et de détecter facilement la provenance d'éventuels problèmes.

    # Vérification du fichier de sortie:
    Nous créons à l'aide de la fonction "create_graph" un graphe que nous entrons dans le fichier "sp.c" qui est notre programme en C, et dans le fichier "sp.py" qui est le programme en Python fourni par les professeurs. 
    Pour tester notre programme, nous comparons par morceaux de plusieurs octets le contenu de notre fichier de sortie avec le fichier de sortie du code python fourni pour vérifier qu'ils soient bien identiques et ainsi s'assurer du bon fonctionnement de notre programme.



## Auteurs
- Camille Lefevbre
- Manon Kummeler





### Guide GitHub :


#### Getting started

To make it easy for you to get started with GitLab, here's a list of recommended next steps.

Already a pro? Just edit this README.md and make it your own. Want to make it easy? [Use the template at the bottom](#editing-this-readme)!

#### Add your files

- [ ] [Create](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#create-a-file) or [upload](https://docs.gitlab.com/ee/user/project/repository/web_editor.html#upload-a-file) files
- [ ] [Add files using the command line](https://docs.gitlab.com/ee/gitlab-basics/add-file.html#add-a-file-using-the-command-line) or push an existing Git repository with the following command:

```
cd existing_repo
git remote add origin https://forge.uclouvain.be/projet-c/projet-c.git
git branch -M main
git push -uf origin main
```

#### Integrate with your tools

- [ ] [Set up project integrations](https://forge.uclouvain.be/projet-c/projet-c/-/settings/integrations)

#### Collaborate with your team

- [ ] [Invite team members and collaborators](https://docs.gitlab.com/ee/user/project/members/)
- [ ] [Create a new merge request](https://docs.gitlab.com/ee/user/project/merge_requests/creating_merge_requests.html)
- [ ] [Automatically close issues from merge requests](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html#closing-issues-automatically)
- [ ] [Enable merge request approvals](https://docs.gitlab.com/ee/user/project/merge_requests/approvals/)
- [ ] [Set auto-merge](https://docs.gitlab.com/ee/user/project/merge_requests/merge_when_pipeline_succeeds.html)

#### Test and Deploy

Use the built-in continuous integration in GitLab.

- [ ] [Get started with GitLab CI/CD](https://docs.gitlab.com/ee/ci/quick_start/index.html)
- [ ] [Analyze your code for known vulnerabilities with Static Application Security Testing (SAST)](https://docs.gitlab.com/ee/user/application_security/sast/)
- [ ] [Deploy to Kubernetes, Amazon EC2, or Amazon ECS using Auto Deploy](https://docs.gitlab.com/ee/topics/autodevops/requirements.html)
- [ ] [Use pull-based deployments for improved Kubernetes management](https://docs.gitlab.com/ee/user/clusters/agent/)
- [ ] [Set up protected environments](https://docs.gitlab.com/ee/ci/environments/protected_environments.html)

***

### Editing this README : 

When you're ready to make this README your own, just edit this file and use the handy template below (or feel free to structure it however you want - this is just a starting point!). Thanks to [makeareadme.com](https://www.makeareadme.com/) for this template.

#### Suggestions for a good README

Every project is different, so consider which of these sections apply to yours. The sections used in the template are suggestions for most open source projects. Also keep in mind that while a README can be too long and detailed, too long is better than too short. If you think your README is too long, consider utilizing another form of documentation rather than cutting out information.

#### Name
Choose a self-explaining name for your project.

#### Description
Let people know what your project can do specifically. Provide context and add a link to any reference visitors might be unfamiliar with. A list of Features or a Background subsection can also be added here. If there are alternatives to your project, this is a good place to list differentiating factors.

#### Badges
On some READMEs, you may see small images that convey metadata, such as whether or not all the tests are passing for the project. You can use Shields to add some to your README. Many services also have instructions for adding a badge.

#### Visuals
Depending on what you are making, it can be a good idea to include screenshots or even a video (you'll frequently see GIFs rather than actual videos). Tools like ttygif can help, but check out Asciinema for a more sophisticated method.

#### Installation
Within a particular ecosystem, there may be a common way of installing things, such as using Yarn, NuGet, or Homebrew. However, consider the possibility that whoever is reading your README is a novice and would like more guidance. Listing specific steps helps remove ambiguity and gets people to using your project as quickly as possible. If it only runs in a specific context like a particular programming language version or operating system or has dependencies that have to be installed manually, also add a Requirements subsection.

#### Usage
Use examples liberally, and show the expected output if you can. It's helpful to have inline the smallest example of usage that you can demonstrate, while providing links to more sophisticated examples if they are too long to reasonably include in the README.

#### Support
Tell people where they can go to for help. It can be any combination of an issue tracker, a chat room, an email address, etc.

#### Roadmap
If you have ideas for releases in the future, it is a good idea to list them in the README.

#### Contributing
State if you are open to contributions and what your requirements are for accepting them.

For people who want to make changes to your project, it's helpful to have some documentation on how to get started. Perhaps there is a script that they should run or some environment variables that they need to set. Make these steps explicit. These instructions could also be useful to your future self.

You can also document commands to lint the code or run tests. These steps help to ensure high code quality and reduce the likelihood that the changes inadvertently break something. Having instructions for running tests is especially helpful if it requires external setup, such as starting a Selenium server for testing in a browser.

#### Authors and acknowledgment
Show your appreciation to those who have contributed to the project.

#### License
For open source projects, say how it is licensed.

#### Project status
If you have run out of energy or time for your project, put a note at the top of the README saying that development has slowed down or stopped completely. Someone may choose to fork your project or volunteer to step in as a maintainer or owner, allowing your project to keep going. You can also make an explicit request for maintainers.
