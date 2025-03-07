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
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fopen
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` freopen
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fclose
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fgetc
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` ungetc
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` getchar
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fgets
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fputc
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` putc
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` putchar
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fputs
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` puts
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fread
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fwrite
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fseek
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

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
