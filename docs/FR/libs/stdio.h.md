## `📚` <stdio.h>

### `⚙️` printf
  ├── **`💡 Affiche du texte formaté sur la sortie standard.`**  
  ├── `🔧 Utilise des spécificateurs (%d, %s, etc.).`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
  char* chaine = "Hello World !"; // Crée une chaine de caractères
  printf("Message: %s", chaine);  // Affiche la chaine de caractères là où ce trouve "%s" (formatage)
  
  return 0;
}
```  

### `⚙️` fprintf
  ├── **`💡 Écrit du texte formaté dans un fichier.`**  
  ├── `🔧 Prend un FILE* en premier argument.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    FILE *fichier = fopen ("fichier.txt", "W");

    fprintf( fichier, "Hello World !" );
    fclose ( fichier                  );

    /*           |> Standard Output
        fprintf( stdout, "Hello World!\n"     ); // équivalent à printf
        fprintf( stderr, "Sortie d'erreur \n" ); // équivalent à perror
                 |> Standard Error
        
    */

    return 0;
}
```  

### `⚙️` sprintf
  ├── **`💡 Écrit du texte formaté dans une chaîne.`**  
  ├── `🔧  Risque de dépassement de tampon (préférer snprintf)`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{

    char tampon[100]; // Buffer (zone mémoire temporaire)
    
    char* chaine = "Hello World !";
    int   entier = 42;
    float reel   = 3.14;

    sprintf(tampon, "Chaine: %s\nEntier: %d\nRéel: %f", chaine, entier, reel); // Ecrit dans le tampon la chaine de caractères formatée
    printf("%s\n", tampon);                                                    // Affiche la chaine de caractères contenue dans le tampon

    return 0;
}
```  

### `⚙️` snprintf
  ├── **`💡 Écrit du texte formaté dans une chaîne avec limite de taille.`**  
  ├── `🔧 Plus sécurisé que sprintf car il limite l'écriture à la taille du buffer (grâce à sizeof(buffer) )`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{

    char tampon[100]; // Buffer (zone mémoire temporaire)
    
    char* chaine = "Hello World !";
    int   entier = 42;
    float reel   = 3.14;

    int tailleBuffer; // Permet de stocker la taille du tampon

    tailleBuffer = snprintf(tampon, sizeof(tampon), "Chaine: %s\nEntier: %d\nRéel: %f", chaine, entier, reel); // sizeof(tampon) = limite de 100 caractères

    // Si la taille du tampon est supérieure ou égale à la taille du tampon
    if (tailleBuffer >= sizeof(tampon))
    {
        printf("Erreur: Buffer overflow\n"); // Dépassement de tampon
        return 1;
    }

    printf("%s\n", tampon);

    return 0;
}
```  

### `⚙️` scanf
  ├── **`💡 Lit des entrées formatées depuis la saisie standard.`**  
  ├── `🔧 Peut causer des erreurs si mal utilisé.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    char message[256];

    printf("Entrez votre message: ");
    scanf("%255s", message);                              // Scan le message entré par l'utilisateur et le stocke dans la variable message

    printf("Affichage du message entré: %s\n", message); // Affiche le message entré par l'utilisateur

    return 0;
}
```  

### `⚙️` fscanf
  ├── **`💡 Lit des entrées formatées depuis un fichier.`**  
  ├── `🔧 Similaire à scanf mais pour les fichiers.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    // CONTENU DE "message.txt": "Hello, World! 1984"

    FILE *fichier = fopen("message.txt", "r"); // Ouverture du fichier en mode lecture
    char message[256];                         // Tableau de caractères pour stocker le message
    int  entier;

    printf("Recherche du message dans le fichier message.txt...\n");
 
    fscanf(fichier, "%s", message);                           // Lecture de la première chaîne de caractères du fichier ("Hello,")
    fscanf(fichier, "%d", &entier);                           // Lecture de l'entier suivant (1984)
    
    printf("Message lu: %s\nEntier lu: %d", message, entier); // Affichage du message et de l'entier

    fclose(fichier); // Fermeture du fichier

    return 0;
}
```

### `⚙️` sscanf
  ├── **`💡 Lit des entrées formatées depuis une chaîne.`**  
  ├── `🔧 Transforme une char* en valeurs formatées.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    char* maChaine = "Chaine 1238";

    char  chaine[100];
    int   nombre;

    sscanf(maChaine, "%s %d"                , chaine, &nombre ); // On récupère la chaine de caractères et le nombre de la chaine "maChaine"
    printf("Ma chaine: %s\nMon nombre: %d\n", chaine,  nombre );

    return 0;
}
```

### `⚙️` fopen
  ├── **`💡 Ouvre un fichier et retourne un pointeur FILE*`**  
  ├── `🔧 Modes : "r" (lecture), "w" (écriture), "a" (ajout), "r+" (lecture et écriture), "w+" (lecture et écriture), "a+" (ajout et lecture)  `  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    FILE *fichier;
    
    fichier = fopen("file.txt", "w");  // Ouvre le fichier en mode écriture

    fprintf(fichier, "Hello World !"); 
    fclose(fichier);                   

    return 0;
}
```

### `⚙️` freopen
  ├── **`💡 Rouvre un fichier en redirigeant un flux existant.`**  
  ├── `🔧 Utile pour rediriger stdin, stdout, etc.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    freopen("output.txt", "w", stdout); // Redirige la sortie standard vers "output.txt"

    printf("Hello, World!\n");          // Au lieu d'afficher dans la console, affiche dans "output.txt"

    fclose(stdout);

    return 0;
}
```


### `⚙️` fclose
  ├── **`💡 Ferme un fichier ouvert.`**  
  ├── `🔧 Nécessaire pour éviter les fuites mémoire.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    FILE *fichier = fopen("fichier_à_fermer.txt", "w");

    fclose(fichier); // Ferme le fichier ouvert (ici, fichier_à_fermer.txt)

    return 0;
}
```

### `⚙️` fgets
  ├── **`💡 Lit une ligne depuis un fichier.`**  
  ├── `🔧 Évite le dépassement de tampon.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    char ligne[256];

    FILE *fichier = fopen("fichier.txt", "r");
    
    while(fgets(ligne, sizeof(ligne), fichier))
    {
        printf("%s", ligne);
    }

    fclose(fichier);

    return 0;
}
```

### `⚙️` fgetc
  ├── **`💡 Lit un caractère depuis un fichier.`**  
  ├── `🔧 Retourne un int pour gérer EOF.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    int caractere;
    FILE *fichier = fopen("fichier.txt", "r");

    while((caractere = fgetc(fichier)) != EOF) // Tant que le caractère n'est pas la fin du fichier (EOF) 
    {                                          // EOF = End Of File (Fin du fichier)
        putchar(caractere);
    }

    return 0;
}
```

### `⚙️` ungetc
  ├── **`💡 Remet un caractère dans le flux d’entrée.`**  
  ├── `🔧 Permet de "revenir en arrière" dans un flux.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    char caractere;

    printf("Entré un caractère: ");
    caractere = getchar();                            // On lit un caractère entré par l'utilisateur
    
    printf("Le caractère entré est: %c", caractere);

    ungetc(stdin, caractere);                         // On remet le caractère dans le flux d'entrée

    caractere = getchar();                            // On peut lire à nouveau le caractère
    printf("Le caractère relu est: %c", caractere);

    return 0;
}
```

### `⚙️` getchar
  ├── **`💡 Lit un caractère depuis stdin.`**  
  ├── `🔧 Identique à getc(stdin)`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    char caractere;

    printf("Entré un caractère: ");
    caractere = getchar();                            // On lit un caractère entré par l'utilisateur

    printf("Le caractère entré est: %c", caractere);  // On affiche le caractère entré

    return 0;
}
```
  

### `⚙️` fputc
  ├── **`💡 Écrit un caractère dans un fichier.`**  
  ├── `🔧 Retourne le caractère écrit ou EOF.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{

    FILE *fichier = fopen("fichier.txt", "w");

    fputc('H', fichier); // Écriture d'un caractère dans le fichier "fichier.txt"
    fclose(fichier);

    fputc('H', stdout); // Écriture d'un caractère dans la sortie standard

    return 0;
}
```

### `⚙️` putc
  ├── **`💡 Similaire à fputc, peut être une macro.`**  
  ├── `🔧 Moins sécurisé que fputc`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    putc('H', stdout); // La même chose que fputc

    return 0;
}
```

### `⚙️` putchar
  ├── **`💡 Écrit un caractère sur stdout.`**  
  ├── `🔧 Identique à putc(c, stdout)`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
    char caractere = 'A';
    putchar(caractere);
 
    return 0;
}
```

### `⚙️` fputs
  ├── **`💡 Écrit une chaîne dans un fichier.`**  
  ├── `🔧 Ne rajoute pas automatiquement de \n`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{

    FILE *fichier = fopen("fichier.txt", "w");

    fputs("Bonjour", fichier); // Ecriture dans le fichier "Bonjour"

    fclose(fichier);
 
    return 0;
}
```

### `⚙️` puts
  ├── **`💡 Écrit une chaîne sur stdout avec \n automatique.`**  
  ├── `🔧 Plus sûr que printf("%s\n", str)`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{

    puts("Puts ne prend en paramètre qu'une chaîne de caractères et ajoute automatiquement un retour à la ligne à la fin de la chaîne.");
    
    return 0;
}
```

### `⚙️` fread
  ├── **`💡 Lit un bloc de données binaires depuis un fichier.`**  
  ├── `🔧 Utilisé pour des fichiers non-textes.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main() {
    FILE *fichier = fopen("fichier.bin", "rb");              // Ouvre en mode lecture binaire

    if (fichier == NULL) {
        printf("Erreur d'ouverture du fichier\n");
        return 1;
    }

    int donnee;
    size_t result = fread(&donnee, sizeof(int), 1, fichier); // Lit un entier du fichier
    // |> Taille de l'objet mémoire à lire

    if (result != 1) {
        printf("Erreur de lecture\n");
    } else {
        printf("Donnée lue : %d\n", donnee);                 // Affiche la donnée lue (voir l'exemple fwrite (donnée lu: 12345))
    }

    fclose(fichier);                                         // Ferme le fichier
    return 0;
}
```

### `⚙️` fwrite
  ├── **`💡 Écrit un bloc de données binaires dans un fichier.`**  
  ├── `🔧  Similaire à fread, mais en écriture.`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main() {
    FILE *fichier = fopen("fichier.bin", "wb");              // Ouvre le fichier en mode écriture binaire
    
    if (fichier == NULL) {
        printf("Erreur d'ouverture du fichier\n");
        return 1;
    }

    int donnee = 12345;                                      // Valeur à écrire
    fwrite(&donnee, sizeof(int), 1, fichier);                // Écrit l'entier dans le fichier

    fclose(fichier);                                         // Ferme le fichier
    printf("Donnée écrite dans fichier.bin: %d\n", donnee); // Affiche la valeur écrite (s'affiche comme ça dans le fichier.bin: 90
```

### `⚙️` fseek
  ├── **`💡 Déplace la position de lecture/écriture dans un fichier.`**  
  ├── `🔧 Modes: "SEEK_SET", "SEEK_CUR", "SEEK_END".`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main() {
    FILE *fichier = fopen("fichier.txt", "r");
    char buffer[50];

    if (fichier == NULL) {
        perror("Erreur d'ouverture du fichier");
        return 1;
    }

    // 1. Utilisation de SEEK_SET: Déplace le curseur à la 10ème position (index 9)
    fseek(fichier, 9, SEEK_SET);
    fgets(buffer, sizeof(buffer), fichier);
    printf("SEEK_SET - Texte à partir de la 10ème position: %s\n", buffer);

    // 2. Utilisation de SEEK_CUR: Déplace le curseur de 5 positions supplémentaires à partir de la position actuelle
    fseek(fichier, 5, SEEK_CUR);
    fgets(buffer, sizeof(buffer), fichier);
    printf("SEEK_CUR - Texte à partir de la position actuelle après déplacement: %s\n", buffer);

    // 3. Utilisation de SEEK_END: Déplace le curseur à 10 positions avant la fin du fichier
    fseek(fichier, -10, SEEK_END);
    fgets(buffer, sizeof(buffer), fichier);
    printf("SEEK_END - Texte à partir de 10 caractères avant la fin: %s\n", buffer);

    // Ferme le fichier
    fclose(fichier);

    // TEXTE DE fichier.txt: Bonjours, ceci est un exemple pour expliquer la fonctions fseek de la lib stdio.h :)
    
    /*
    RÉSULTAT ATTENDU:

    SEEK_SET - Texte à partir de la 10ème position:  ceci est un exemple pour expliquer la fonctions 
    SEEK_CUR - Texte à partir de la position actuelle après déplacement:  de la lib stdio.h :)
    SEEK_END - Texte à partir de 10 caractères avant la fin: stdio.h :)
    */

    return 0;
}
```

### `⚙️` ftell
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` rewind
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fflush
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` remove
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` rename
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` tmpfile
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` tmpnam
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` perror
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` clearerr
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` feof
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` ferror
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` setvbuf
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` setbuf
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :
