# ft_printf

Recréation simplifiée de la fonction `printf` de la bibliothèque standard C. Ce projet de l’école 42 apprend à traiter une chaîne de format, à récupérer des arguments variadiques et à afficher des valeurs avec `write`.

## Fonctionnalités

La fonction `ft_printf` écrit sur la sortie standard et renvoie le nombre de caractères affichés. Les conversions prises en charge sont :

| Conversion | Valeur affichée |
| --- | --- |
| `%c` | Un caractère |
| `%s` | Une chaîne de caractères (`(null)` si le pointeur vaut `NULL`) |
| `%p` | Une adresse en hexadécimal, préfixée par `0x` (`(nil)` si elle est nulle) |
| `%d`, `%i` | Un entier décimal signé |
| `%u` | Un entier décimal non signé |
| `%x` | Un entier en hexadécimal minuscule |
| `%X` | Un entier en hexadécimal majuscule |
| `%%` | Le caractère `%` |

Les indicateurs de formatage, la largeur de champ et la précision ne sont pas implémentés. Pour un spécificateur autre que ceux listés ci-dessus, son caractère est écrit tel quel.

## Compilation

Depuis le dossier du projet :

```sh
cd ft_printf
make
```

La compilation produit la bibliothèque statique `libftprintf.a`. Les commandes Makefile disponibles sont `make`, `make clean`, `make fclean` et `make re`. La compilation utilise `gcc` avec `-Wall -Wextra -Werror`.

## Utilisation

Inclure l’en-tête puis lier la bibliothèque lors de la compilation de votre programme :

```c
#include "ft_printf.h"

int main(void)
{
	int count;

	count = ft_printf("Bonjour %s, score : %d%%\n", "42", 100);
	return (count < 0);
}
```

Depuis la racine du dépôt, en supposant que le fichier s’appelle `main.c` :

```sh
gcc -Wall -Wextra -Werror -Ift_printf main.c ft_printf/libftprintf.a -o demo
./demo
```

## Organisation du projet

- `ft_printf/ft_printf.c` — parcours de la chaîne de format, lecture des arguments variadiques et dispatch des conversions.
- `ft_printf/ft_utils.c` — affichage des caractères, chaînes et nombres signés dans une base donnée.
- `ft_printf/ft_putunbr.c` — conversion et affichage des entiers non signés.
- `ft_printf/ft_putptr.c` — affichage des pointeurs en hexadécimal.
- `ft_printf/ft_printf.h` — déclarations des fonctions et inclusions nécessaires.
- `ft_printf/Makefile` — compilation de la bibliothèque statique.