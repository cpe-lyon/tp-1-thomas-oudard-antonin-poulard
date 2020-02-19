# Tp 1 Admin systéme

## Manuel

1. A l’aide du manuel, identifiez le rôle de la commande which

    ```bash
    man which
    ```

    ```txt
    DESCRIPTION
        which  renvoie le chemin des fichiers (ou liens) qui seraient exécutés  
        dans l'environnement courant si ses arguments avaient été donnés comme  
        commandes dans un interpréteur de commandes  strictement  conforme  à  
        POSIX. Pour  ce  faire, which cherche dans la variable PATH les fichiers  
        exécutables correspondant aux noms des arguments. which ne normalise pas  
        les chemins.
    ```

2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme option dans la page de manuel de which ?

    ```txt
    Dans le manuel, /pattern où pattern = valeur recherché
    ```

3. Comment quitte-t-on le manuel ?

    ```txt
    On appuye sur 'q' dans le manuel
    ```

4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la première page de la section 6 ; de quoi parle cette section ?

## Navigation dans l’arborescence des fichiers

1. Allez dans le dossier ```/var/log```

    ```bash
    cd /var/log
    ```

2. Remontez dans le dossier parent ```/var``` en utilisant un chemin relatif

    ```bash
    cd ..
    ```

3. Retournez dans le dossier personnel

    ```bash
    cd ~
    ```

4. Revenez au dossier précédent ```/var``` sans utiliser de chemin

    ```bash
    cd -
    ```

5. Essayez d’accéder au dossier ```/root```, que se passe-t-il ?

    ```bash
    -bash: cd: /root: Permission denied
    ```

6. Essayez la commande ```sudo cd /root```, que se passe-t-il ? Expliquez

    ```txt
    [sudo] password for *******:
    sudo: cd: command not found  

    cd attend un executable. cd n'est pas un executable
    ```

7. A partir de votre dossier personnel, créez l’arborescence suivante :

    ```bash
    mkdir ~/Dossier1
    touch ~/Dossier1/Fichier1
    mkdir ~/Dossier2
    mkdir ~/Dossier2/Dossier2.1
    mkdir ~/Dossier2/Dossier2.2
    touche ~/Dossier2/Dossier2.2/Fichier2
    touche ~/Dossier2/Dossier2.2/Fichier3
    ```

8. Revenez dans votre dossier personnel ; à l’aide de la commande ```rm```, essayez de supprimer Fichier1, puis Dossier1 ; que se passe-t-il ?

    ```bash
    rm ~/Dossier1/Fichier1
    rm ~/Dossier1

    rm: cannot remove 'Dossier1': Is a directory
    ```

9. Quelle commande permet de supprimer un dossier ?

    ```bash
    rmdir ~/Dossier1
    ```

10. Que se passe-t-il quand on applique cette commande à Dossier2 ?

    ```bash
    rmdir ~/Dossier2
    rmdir: failed to remove 'Dossier2': Directory not empty
    ```

11. Comment supprimer en une seule commande Dossier2 et son contenu ?

    ```bash
    rm -R ~/Dossier2
    ```

## Commandes importantes

1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ?

    ```bash
    date
    jeudi 13 février 2020, 15:46:17 (UTC+0000)
    ```

    ```txt
    DESCRIPTION
       time run the program COMMAND with any given arguments ARG....  When COMMAND finishes,
       time displays information about resources used by COMMAND
    ```

2. Dans votre dossier personnel, tapez successivement les commandes ```ls``` puis ```la```,
que peut-on en déduire sur les fichiers commençant par un point ?

    ```txt
    ls affiche les dossiers/fichiers du repertoire courant.
    la affiche les dossiers/fichiers du repertoire courant ainsi que les dossiers/fichiers cachés.
    ```
3. Où se situe le programme ls ?
    
    ```txt
    whereis ls
    ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz
    ```

4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande.
    
    ```txt
    ll
    total 48
    drwxr-xr-x 6 antonin antonin 4096 Feb 13 16:19 ./
    drwxr-xr-x 3 root    root    4096 Feb 13 14:14 ../
    -rw------- 1 antonin antonin  706 Feb 13 15:50 .bash_history
    -rw-r--r-- 1 antonin antonin  220 May  5  2019 .bash_logout
    -rw-r--r-- 1 antonin antonin 3771 May  5  2019 .bashrc
    drwx------ 2 antonin antonin 4096 Feb 13 14:18 .cache/
    drwxrwxr-x 2 antonin antonin 4096 Feb 13 15:40 Dossier1/
    drwx------ 3 antonin antonin 4096 Feb 13 14:18 .gnupg/
    -rw------- 1 antonin antonin   36 Feb 13 15:17 .lesshst
    drwxrwxr-x 3 antonin antonin 4096 Feb 13 15:51 .local/
    -rw-rw-r-- 1 antonin antonin    3 Feb 13 16:14 plop
    -rw-r--r-- 1 antonin antonin  807 May  5  2019 .profile
    -rw-r--r-- 1 antonin antonin    0 Feb 13 14:18 .sudo_as_admin_successful

    Alias
    alias ll='ls -alF'
    ```

5. Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ?
    
    ```txt
    ls /bin
    ```

6. Que fait la commande ls .. ?
    
    ```txt
    Elle liste les fichiers dans le répertoire actuel
    ```

7. Quelle commande donne le chemin complet du dossier courant ?
    
    ```txt
    pwd
    /home/antonin
    ```

8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?
    
    ```txt
    Elle écrit yo dans un fichier nommé plop (> écrit dans le fichier donc peu importe le nombre de fois qu’on éxécute la commande il       n’y aura qu’un ‘yo’.
    ```

9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?
    
    ```txt
    Elle écrit yo yo dans un fichier (>> ajoute dans le fichier donc on aura autant de ‘yo’ que d’éxécutions de la commande)
    ```


10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.
    
    ```txt
    file plop
    plop: ASCII text

    Elle donne le type de fichier
    ```
    
11. Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier
avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi :
qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ?
    
    ```txt
    echo 'Hello Toto !' > toto
    ln toto titi
    titi existe toujours malgré que toto soit supprimé
    ```

12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le
contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle
conséquence cela a-t-il sur tutu ?
    
    ```txt
    Tutu a été modifié aussi (enfin pas vraiment étant donné que ce n’est pas un fichier en soi)
    Une fois le fichier titi supprimé tutu existe toujours mais ne pointe sur rien, il est donc vide.
    ```
