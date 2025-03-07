## `📚` <stdio.h>

### `⚙️` printf
  ├── **`💡 Affiche du texte formaté sur la sortie standard.`**  
  ├── `🔧 Utilise des spécificateurs (%d, %s, etc.).`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{
  char* chaine = "Hello World !";
  printf("Message: %s", chaine);
  
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
  ├── `🔧  Risque de dépassement de tampon, préférer snprintf`  
  └── **Exemple d'utilisation** :

```c
#include <stdio.h>

int main()
{

    char tableau[100]; // crée un tableau de 100 caractères
    
    char* chaine = "Hello World !";
    int   entier = 42;
    float reel   = 3.14;

    sprintf(tableau, "Chaine: %s\nEntier: %d\nRéel: %f", chaine, entier, reel); // Formate les données dans le tableau
    printf("%s\n", tableau);                                                    // Affiche le tableau

    return 0;
}
```

### `⚙️` snprintf
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` scanf
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

### `⚙️` fscanf
  ├── **`💡`**  
  ├── `🔧`  
  └── **Exemple d'utilisation** :

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
