# Test-de-recrutement-Ifollow-profile-deploiement



Prérequis (temps passé 4H)

Avoir Ubuntu 20.04.
Avoir installé ROS noetic sur votre ordinateur.    
    

Installation

Télécharger le projet sur votre ordinateur en clonant le dépôt Github. 


Exercice 1 :(temps passé 1h30)

Pour l'installation et l'utilisation du turtlebot3, je vous invite à utiliser ce lien :
https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/

Voici les commandes principales de cet exercice, exécuter les chacune dans un terminal différent :

Pour commencer : lancer le noeud ROS master en utilisant la commande :

        $roscore 

Pour ouvrir le monde en simulation:

    $roslaunch turtlebot3_gazebo turtlebot3_world.launch
    
Afin de contrôler le robot avec les touches de votre clavier:

    $roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    
Pour contrôler le robot en lui indiquant un nav goal 2D

    $roslaunch turtlebot3_navigation turtlebot3_navigation.launch 
    
ATTENTION , une fois lancer veuillez placer la position du robot ( visible sur gazebo) à l'aide de la fleche verte sur rviz.Puis maintenant vous pouvez utiliser la fleche rose pour définir un goal au robot.    


Exercice 2 :(temps passé 1h30)

Exécuter la commande suivante :

    $rosrun ifollow multiplexer.py
    
Pour choisir le mode contrôle  web, exécuter cette commande :

    $rostopic pub /change_origin_cmd std_msgs/String 'web'
    
Ou alors, pour choisir le mode contrôle  local, exécuter cette commande :

    $rostopic pub /change_origin_cmd std_msgs/String 'local'
    
Ou encore, pour avoir les deux, exécuter cette commande  : 

    $rostopic pub /change_origin_cmd std_msgs/String 'both'  

Excercice 3:(temps passé 4h15)

J'ai suivi ce tuto afin d'installer le broker MQTT : https://www.vultr.com/docs/install-mosquitto-mqtt-broker-on-ubuntu-20-04-server/

Pour démarrer le broker:

    $sudo systemctl start mosquitto

Il sera également nécessaire d'installer ncurses :
   
    $sudo apt-get install libncurses5-dev libncursesw5-dev

Vous pouvez exécuter la commande suivante pour lancer le programme coté simulateur:
   
    $rosrun ifollow listener_mqtt_ros.py 

programme coté client (en étant dans le répertoire ifollow/src$) :

    $g++ publisher_mqtt.cpp -lmosquitto -lncurses -o publisher   
    $./publisher

Exercice 4:(temps passé 4h)

J'ai suivi ce tuto afin d'installer opencv: https://vegastack.com/tutorials/how-to-install-opencv-on-ubuntu-20-04/

Nous devions utilser les  AR-TAG apriltags, j'ai  utilisé ce tuto pour me familiariser à leur utilisation: https://pyimagesearch.com/2020/11/02/apriltag-with-python/

J'ai également dû rogner légèrement les jpg fournies afin d'éviter une erreur lors de l'analyse (warning: too many borders in contour_detect (max of 32767!)
   
Vous pouvez exécuter la commande suivante (en étant dans le répertoire ifollow/src$) pour lancer le programme analysant l'image 1:

    $python3 ifollow tag.py -i ar_tag_1.JPG  
   
Les ID des tags étaient 20,21,22 et je leur ai attribué des coordonées tels que (1,2,1)/ (-1,2,1) / (1,-2,1).
  

Auteur

Eloi Guerbet


