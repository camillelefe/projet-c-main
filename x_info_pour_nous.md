# Informations utiles à se partager #

## build  
Pour créer le build, il faut utiliser la commande cmake : "cmake -S . -B build"
Si on ajoute de nouveaux fichiers source à notre projet, 
on devra les inclure dans le fichier CMakeLists.txt en utilisant la fonction "add_executable". 
Ensuite, on devra régénérer les fichiers de build en exécutant à nouveau la commande cmake : "cmake -S . -B build"


## compiler
Pour compiler le projet, faire les commandes suivantes : 
cd build
make

Pour executer l'executable, faire la commande suivante : 
./executable_main 


## structure 
structures des includes (liens entres les fichiers) :

                main.c
                  |       test.c
                  v         |
                code.c  < -- 
                  |
                  v
               struct.h
                  |
                  v
           les librairies