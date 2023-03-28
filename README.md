
## indice

| Level 0                   | Level 1                       | Level 2         | Level 3        |
|---------------------------|-------------------------------|-----------------|----------------|
| [ft_putstr](#ft_putstr)   | [inter](#inter)               |
| [ft_strlen](#ft_strlen)   | [reverse_bits](#reverse_bits) |
| [rev_print](#rev_print)   | [wdmatch](#wdmatch)           |
| [first_word](#first_word) | [alpha_mirror](#alpha_mirror) |
| [fizzbuzz](#fizzbuzz)     | [atoi](#atoi)                 |
| [ft_strcpy](#ft_strcpy)   | [camel_to_snake](#camel_to_snake) |
| [ft_swap](#ft_swap)       | [do_op](#do_op)               |
| [repeat_alpha](#repeat_alpha) | [ft_strcspn](#ft_strcspn) |
| [rot_13](#rot_13)         | [ft_strdup](#ft_strdup)       |
| [rotone](#rotone)         | [ft_strpbrk](#ft_strpbrk)     |
| [search_and_replace](#search_and_replace) | [ft_strrev](#ft_strrev) |
| [ulstr](#ulstr)           | [ft_strspn](#ft_strspn)       |
|                           | [is_power_of_2](#is_power_of_2) |
|                           | [last_word](#last_word)         |
|                           | [max](#max)                     |
|                           | [print_bits](#print_bits)       |
|                           | [snake_to_camel](#snake_to_camel) |
|                           | [strcmp](#strcmp)               |
|                           | [swap_bits](#swap_bits)         |
|                           | [union](#union)                 |


# Level 0

## ft_putstr
<details>
  <summary>subject</summary>

```txt
Assignment name  : ft_putstr
Expected files   : ft_putstr.c
Allowed functions: write
--------------------------------------------------------------------------------

Write a function that displays a string on the standard output.

The pointer passed to the function contains the address of the string's first
character.

Your function must be declared as follows:

void	ft_putstr(char *str);
```
</details>

```c
#include <unistd.h>

void	ft_putstr(char *str)
{
	int i = -1;
	while(str[++i])
		write(1, &str[i], 1);
}
```
```c
int	main(void)
{
	ft_putstr("42 Barcelona");
}
```
	$42 Barcelona

## ft_strlen

<details>
  <summary>subject</summary>

```txt
Assignment name  : ft_strlen
Expected files   : ft_strlen.c
Allowed functions: 
--------------------------------------------------------------------------------

Write a function that returns the length of a string.

Your function must be declared as follows:

int	ft_strlen(char *str);

```
</details>

```c
int	ft_strlen(char *str)
{
	int	i = 0;

	while(str[i])
		i++;
	return(i);
}
```
```c
#include <unistd.h>
#include <stdio.h>
int	main(void)
{
	int	len;

	len = ft_strlen("42 Barcelona");
	printf("len: %d", len);
}
```
	$len: 12

[Indice](#indice)

## rev_print

<details>
<summary>subject</summary>

	Assignment name  : rev_print
	Expected files   : rev_print.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string, and displays the string in reverse followed by a newline.

	If the number of parameters is not 1, the program displays a newline.

	Examples:

	$> ./rev_print "zaz" | cat -e
	zaz$
	$> ./rev_print "dub0 a POIL" | cat -e
	LIOP a 0bud$
	$> ./rev_print | cat -e
	$
</details>

```c
#include <unistd.h>

int	ft_len(char *str)
{
	int i = 0;

	while(str[i])
		i++;
	return (i);
}

int main(int n, char **str)
{
	if(n == 2)
	{
		int len = ft_len(str[1]) - 1;

		while(len >= 0)
		{
			write(1, &str[1][len], 1);
			len--;
		}
	}
	write(1, "\n", 1);
	return (0);
}
```

[Indice](#indice)

## first_word
<details>
<summary>subject</summary>

	Assignment name  : first_word
	Expected files   : first_word.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays its first word, followed by a newline.

	A word is a section of string delimited by spaces/tabs or by the start/end of the string.

	If the number of parameters is not 1, or if there are no words, simply display a newline.

	Examples:

	$> ./first_word "FOR PONY" | cat -e
	FOR$
	$> ./first_word "this        ...       is sparta, then again, maybe    not" | cat -e
	this$
	$> ./first_word "   " | cat -e
	$
	$> ./first_word "a" "b" | cat -e
	$
	$> ./first_word "  lorem,ipsum  " | cat -e
	lorem,ipsum$
	$>
</details>

```c
#include <unistd.h>

int	main(int n, char **str)
{
	if(n == 2)
	{
		while(*str[1] == ' ')
			str[1]++;
		int i = 0;
		while(str[1][i] != ' ' && str[1][i] != '\0')
		{
			write(1, &str[1][i], 1);
			i++;
		}
		
	}
	write(1, "\n", 1);
	return(0);
}
```
[Indice](#indice)

## fizzbuzz
<details>
<summary>subject</summary>

	Assignment name  : fizzbuzz
	Expected files   : fizzbuzz.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that prints the numbers from 1 to 100, each separated by a newline.

	If the number is a multiple of 3, it prints 'fizz' instead.

	If the number is a multiple of 5, it prints 'buzz' instead.

	If the number is both a multiple of 3 and a multiple of 5, it prints 'fizzbuzz' instead.

	Example:

	$>./fizzbuzz
	1
	2
	fizz
	4
	buzz
	fizz
	7
	8
	fizz
	buzz
	11
	fizz
	13
	14
	fizzbuzz
	[...]
	97
	98
	fizz
	buzz
	$>

</details>

```c
void static	ft_number(int n)
{
	if(n > 9)
		ft_number(n / 10);
	write(1, &"0123456789"[n % 10], 1);
}

int	main(void)
{
	int	i = 1;

	while(i <= 100)
	{
		if (i % 3 == 0 && i %5  == 0)
			write(1, "fizzbuzz", 8);
		else if ( i % 3 == 0)
			write(1, "fizz", 4);
		else if ( i % 5 == 0)
			write(1, "buzz", 4);
		else
			ft_number(i);
		write(1, "\n", 1);
		i++;
	}
}
```

[Indice](#indice)

## ft_strcpy
<details>
<summary>subject</summary>

	Assignment name  : ft_strcpy
	Expected files   : ft_strcpy.c
	Allowed functions: 
	--------------------------------------------------------------------------------

	Reproduce the behavior of the function strcpy (man strcpy).

	Your function must be declared as follows:

	char    *ft_strcpy(char *s1, char *s2);

</details>

```c
char    *ft_strcpy(char *s1, char *s2)
{
    int i = 0;
    
    while(s2[i])
    {
        s1[i] = s2[i];
        i++;
    }
    
    s1[i] = '\0';
    return (s1);
}
```

```c
#include <string.h>
#include <stdio.h>

int main(void)
{
  char dst[] = "42 Barcelona";
  char str[] = "copiar";
  printf("dst: %s, str: %s\n", dst, str);
  ft_strcpy(dst, str);
  printf("dst: %s, str: %s\n", dst, str);
}
```
	$dst: 42 Barcelona, str: copiar	
	$dst: copiar, str: copiar

[Indice](#indice)

## ft_swap
<details>
<summary>subject</summary>

	Assignment name  : ft_swap
	Expected files   : ft_swap.c
	Allowed functions: 
	--------------------------------------------------------------------------------

	Write a function that swaps the contents of two integers the adresses of which are passed as parameters.

	Your function must be declared as follows:

	void	ft_swap(int *a, int *b);

</details>

```c
void	ft_swap(int *a, int *b)
{
	int tmp;
	
	tmp = *a;
	*a = *b;
	*b = tmp;
}
```

```c
#include <stdio.h>

int	main(void)
{
	int a = 42;
	int b = 20;

	printf("a:%d, b:%d \n", a ,b);
	ft_swap(&a, &b);
	printf("a:%d, b:%d \n", a ,b);
}
```
	$a:42, b:20
	$a:20, b:42

[Indice](#indice)

## repeat_alpha
<details>
<summary>subject</summary>

	Assignment name  : repeat_alpha
	Expected files   : repeat_alpha.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program called repeat_alpha that takes a string and display it repeating each alphabetical character as many times as its alphabetical index, followed by a newline.

	'a' becomes 'a', 'b' becomes 'bb', 'e' becomes 'eeeee', etc...

	Case remains unchanged.

	If the number of arguments is not 1, just display a newline.

	Examples:

	$>./repeat_alpha "abc"
	abbccc
	$>./repeat_alpha "Alex." | cat -e
	Alllllllllllleeeeexxxxxxxxxxxxxxxxxxxxxxxx.$
	$>./repeat_alpha 'abacadaba 42!' | cat -e
	abbacccaddddabba 42!$
	$>./repeat_alpha | cat -e
	$
	$>
	$>./repeat_alpha "" | cat -e
	$
	$>
</details>

```c
#include <unistd.h>
void rep(char c, int rep)
{
	int i = 0;
	while(i < rep)
	{
		write(1, &c, 1);
		i++;
	}
}


int	main(int n, char **str)
{
	if(n == 2)
	{
		int i = 0;
		while(str[1][i])
		{
			if(str[1][i] >= 'A' && str[1][i] <= 'Z')
				rep(str[1][i], (int)str[1][i] - 64);
			else if(str[1][i] >= 'a' && str[1][i] <= 'z')
				rep(str[1][i], (int)str[1][i] - 96);
			else
				write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
}
```

[Indice](#indice)

## rot_13

<details>
<summary>subject</summary>

	Assignment name  : rot_13
	Expected files   : rot_13.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays it, replacing each of its letters by the letter 13 spaces ahead in alphabetical order.

	'z' becomes 'm' and 'Z' becomes 'M'. Case remains unaffected.

	The output will be followed by a newline.

	If the number of arguments is not 1, the program displays a newline.

	Example:

	$>./rot_13 "abc"
	nop
	$>./rot_13 "My horse is Amazing." | cat -e
	Zl ubefr vf Nznmvat.$
	$>./rot_13 "AkjhZ zLKIJz , 23y " | cat -e
	NxwuM mYXVWm , 23l $
	$>./rot_13 | cat -e
	$
	$>
	$>./rot_13 "" | cat -e
	$
	$>

</details>

```c
#include <unistd.h>

int	main(int a, char **str)
{
	int i = 1;

	if(a <= 1)
		write(1, "\n", 1);
	while(i < a)
	{
		int j = 0;
		while(str[i][j] != '\0')
		{
			if((str[i][j] >= 'a' && str[i][j] <= 'm') \
					|| (str[i][j] >= 'A' && str[i][j] <= 'M'))
				str[i][j] += 13;
			else if((str[i][j] >= 'n' && str[i][j] <= 'z') \
					|| (str[i][j] >= 'N' && str[i][j] <= 'Z'))
				str[i][j] -= 13;
			write(1, &str[i][j], 1);
			j++;
		}
		i++;
	}
}
```

[Indice](#indice)

## rotone
<details>
<summary>subject</summary>

	Assignment name  : rotone
	Expected files   : rotone.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays it, replacing each of its
	letters by the next one in alphabetical order.

	'z' becomes 'a' and 'Z' becomes 'A'. Case remains unaffected.

	The output will be followed by a \n.

	If the number of arguments is not 1, the program displays \n.

	Example:

	$>./rotone "abc"
	bcd
	$>./rotone "Les stagiaires du staff ne sentent pas toujours tres bon." | cat -e
	Mft tubhjbjsft ev tubgg of tfoufou qbt upvkpvst usft cpo.$
	$>./rotone "AkjhZ zLKIJz , 23y " | cat -e
	BlkiA aMLJKa , 23z $
	$>./rotone | cat -e
	$
	$>
	$>./rotone "" | cat -e
	$
	$>

</details>

```c
#include <unistd.h>

int	main(int n, char **str)
{

	if(n  == 2)
	{
		int i = 0;
		while(str[1][i])
		{
			if ((str[1][i] >= 'a' && str[1][i] <= 'y') || (str[1][i] >= 'A' && str[1][i] <= 'Y'))
				str[1][i] += 1;
			if((str[1][i] == 'z') || (str[1][i] == 'Z'))
				str[1][i] -= 25;
			write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
	return (0);
}
```

[Indice](#indice)

## search_and_replace

<details>
<summary>subject</summary>

Assignment name  : search_and_replace
Expected files   : search_and_replace.c
Allowed functions: write, exit
--------------------------------------------------------------------------------

	Write a program called search_and_replace that takes 3 arguments, the first 
	arguments is a string in which to replace a letter (2nd argument) by
	another one (3rd argument).

	If the number of arguments is not 3, just display a newline.

	If the second argument is not contained in the first one (the string)
	then the program simply rewrites the string followed by a newline.

	Examples:
	$>./search_and_replace "Papache est un sabre" "a" "o"
	Popoche est un sobre
	$>./search_and_replace "zaz" "art" "zul" | cat -e
	$
	$>./search_and_replace "zaz" "r" "u" | cat -e
	zaz$
	$>./search_and_replace "jacob" "a" "b" "c" "e" | cat -e
	$
	$>./search_and_replace "ZoZ eT Dovid oiME le METol." "o" "a" | cat -e
	ZaZ eT David aiME le METal.$
	$>./search_and_replace "wNcOre Un ExEmPle Pas Facilw a Ecrirw " "w" "e" | cat -e
	eNcOre Un ExEmPle Pas Facile a Ecrire $

</details>

```c
int	main(int n, char **str)
{
	if(n == 4)
	{
		if(str[2][1] != '\0' || str[3][1] != '\0')
		{	
			write(1, "\n", 1);
			return (0);
		}
		int i = 0;
		while(str[1][i])
		{
			if(str[1][i] == str[2][0])
				str[1][i] = str[3][0];
			write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
	return (0);
}
```

[Indice](#indice)

## ulstr
<details>
<summary>subject</summary>

	Assignment name  : ulstr
	Expected files   : ulstr.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and reverses the case of all its letters.
	Other characters remain unchanged.

	You must display the result followed by a '\n'.

	If the number of arguments is not 1, the program displays '\n'.

	Examples :

	$>./ulstr "L'eSPrit nE peUt plUs pRogResSer s'Il staGne et sI peRsIsTent VAnIte et auto-justification." | cat -e
	l'EspRIT Ne PEuT PLuS PrOGrESsER S'iL STAgNE ET Si PErSiStENT vaNiTE ET AUTO-JUSTIFICATION.$
	$>./ulstr "S'enTOuRer dE sECreT eSt uN sIGnE De mAnQuE De coNNaiSSanCe.  " | cat -e
	s'ENtoUrER De SecREt EsT Un SigNe dE MaNqUe dE COnnAIssANcE.  $
	$>./ulstr "3:21 Ba  tOut  moUn ki Ka di KE m'en Ka fe fot" | cat -e
	3:21 bA  ToUT  MOuN KI kA DI ke M'EN kA FE FOT$
	$>./ulstr | cat -e
	$

</details>

```c
#include <unistd.h>

int	main(int n, char **str)
{
	if(n == 2)
	{
		int i = 0;
		while(str[1][i])
		{
			if(str[1][i] >= 'A' && str[1][i] <= 'Z')
				str[1][i] += 32;
		 	else if(str[1][i] >= 'a' && str[1][i] <= 'z')
				str[1][i] -= 32;
			write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
	return(0);
}
```
# Level 1

[Indice](#indice)

## inter

<details>
<summary>subject</summary>

	Assignment name  : inter
	Expected files   : inter.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes two strings and displays, without doubles, the
	characters that appear in both strings, in the order they appear in the first
	one.

	The display will be followed by a \n.

	If the number of arguments is not 2, the program displays \n.

	Examples:

	$>./inter "padinton" "paqefwtdjetyiytjneytjoeyjnejeyj" | cat -e
	padinto$
	$>./inter ddf6vewg64f gtwthgdwthdwfteewhrtag6h4ffdhsd | cat -e
	df6ewg4$
	$>./inter "rien" "cette phrase ne cache rien" | cat -e
	rien$
	$>./inter | cat -e
	$

</details>

```c
#include <unistd.h>

int	main(int n, char **str)
{
	if(n == 3)
	{
		int arr[255] = {0};
		int i = 0;

		while(str[2][i])
		{
			arr[(int)str[2][i]] = 1;
			i++;
		}
		i = 0;
		while(str[1][i])
		{
			if(arr[(int)str[1][i]])
			{
				write(1, &str[1][i], 1);
				arr[(int)str[1][i]] = 0;
			}
			i++;
		}
	}
	write(1, "\n", 1);
	return(0);
}
```

[Indice](#indice)

## reverse_bits
<details>
<summary>subject</summary>

	Assignment name  : reverse_bits
	Expected files   : reverse_bits.c
	Allowed functions:
	--------------------------------------------------------------------------------

	Write a function that takes a byte, reverses it, bit by bit (like the
	example) and returns the result.

	Your function must be declared as follows:

	unsigned char	reverse_bits(unsigned char octet);

	Example:

	1 byte
	_____________
	0100  0001
	    ||
	    \/
	1000  0010

</details>

```c

unsigned char	reverse_bits(unsigned char octet)
{
	unsigned char out = 0;

	out += ((octet & 128) >> 7);
	out += ((octet & 64) >> 5);
	out += ((octet & 32) >> 3);
	out += ((octet & 16) >> 1);
	out += ((octet & 8) << 1);
	out += ((octet & 4) << 3);
	out += ((octet & 2) << 5);
	out += ((octet & 1) << 7);

	return(out);
}
```
```c
#include <stdio.h>
#include <stdlib.h>

int	main(int n, char **str)
{
	unsigned char ori = atoi(str[1]);
//	unsigned char ori = 32;
	printf("ori: %u\n", ori);
	printf("rev: %u\n", reverse_bits(ori));
}
```

[Indice](#indice)

## wdmatch
<details>
<summary>subject</summary>

	Assignment name  : wdmatch
	Expected files   : wdmatch.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes two strings and checks whether it's possible to
	write the first string with characters from the second string, while respecting
	the order in which these characters appear in the second string.

	If it's possible, the program displays the string, followed by a \n, otherwise
	it simply displays a \n.

	If the number of arguments is not 2, the program displays a \n.

	Examples:

	$>./wdmatch "faya" "fgvvfdxcacpolhyghbreda" | cat -e
	faya$
	$>./wdmatch "faya" "fgvvfdxcacpolhyghbred" | cat -e
	$
	$>./wdmatch "forty two" "qfqfsoudf arzgrsayns tsryegftdgs sjytwdekuooixq " | cat -e
	forty two$
	$>./wdmatch "error" rrerrrfiiljdfxjyuifrrvcoojh | cat -e
	$
	$>./wdmatch | cat -e
	$

</details>

```c
void	wdmatch(char *s1, char *s2)
{
	int i = 0;
	while (s1[i])
	{
		while (*s2 != s1[i] && *s2 != '\0')
			++s2;
		if (*s2 == '\0')
			return;
		++i;
		++s2;
	}
	write(1, s1, i);
}

int		main(int n, char **str)
{
	if (n == 3)
		wdmatch(str[1], str[2]);

	write(1, "\n", 1);
	return (0);
}
```

[Indice](#indice)

## alpha_mirror

<details>
<summary>subject</summary>

	intAssignment name  : alpha_mirror
	Expected files   : alpha_mirror.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program called alpha_mirror that takes a string and displays this string
	after replacing each alphabetical character by the opposite alphabetical
	character, followed by a newline.

	'a' becomes 'z', 'Z' becomes 'A'
	'd' becomes 'w', 'M' becomes 'N'

	and so on.

	Case is not changed.

	If the number of arguments is not 1, display only a newline.

	Examples:

	$>./alpha_mirror "abc"
	zyx
	$>./alpha_mirror "My horse is Amazing." | cat -e
	Nb slihv rh Znzarmt.$
	$>./alpha_mirror | cat -e
	$
	$>

</details>

```c
#include <unistd.h>

int	main(int n, char **str)
{
	if(n == 2)
	{
		int i = 0;
		while(str[1][i] != '\0')
		{
			if(str[1][i] >= 'a' && str[1][i] <= 'z')
				str[1][i] = 'm' - (str[1][i] - 'n');
			if(str[1][i] >= 'A' && str[1][i] <= 'Z')
				str[1][i] = 'M' - (str[1][i] - 'N');
			write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
	return(0);
}
```

[Indice](#indice)

## atoi

<details>
<summary>subject</summary>

	Assignment name  : ft_atoi
	Expected files   : ft_atoi.c
	Allowed functions: None
	--------------------------------------------------------------------------------

	Write a function that converts the string argument str to an integer (type int)
	and returns it.

	It works much like the standard atoi(const char *str) function, see the man.

	Your function must be declared as follows:

	int	ft_atoi(const char *str);

</details>

```c
int ft_atoi(const char *str)
{
	int i = 0;
	int neg = 1;
	int num = 0;

	if (str[i] == '-')
		neg = -1;
	if (str[i] == '-' || str[i] == '+')
		i++;
	while (str[i] != '\0' && str[i] >= '0' && str[i] <= '9')
	{
		num *= 10;
		num += str[i] - '0';
		i++;
	}
	return (neg * num);
}
```
```c
#include <stdio.h>
#include <limits.h>

int main(void)
{
	printf("ori: %i\n", atoi("4294967295"));
	printf("ori: %i\n", atoi("-2147483647"));
	printf("ori: %i\n", atoi("OH ! 13232!"));
	printf("ori: %i\n", atoi("13232"));
	printf("ori: %i\n", atoi("+13232"));
	printf("ori: %i\n", atoi("-13232"));
	printf("ori: %i\n", atoi("-42abc"));
	printf("\t%d\n", INT_MAX);
	printf("\t%d\n", INT_MIN);

	printf("mio: %i\n", ft_atoi("4294967295"));
	printf("mio: %i\n", ft_atoi("-2147483647"));
	printf("mio: %i\n", ft_atoi("OH ! 13232!"));
	printf("mio: %i\n", ft_atoi("13232"));
	printf("mio: %i\n", ft_atoi("+13232"));
	printf("mio: %i\n", ft_atoi("-13232"));
	printf("mio: %i\n", ft_atoi("-42abc"));
}
```
	ori: -1
	ori: -2147483647
	ori: 0
	ori: 13232
	ori: 13232
	ori: -13232
	ori: -42
		2147483647
		-2147483648
	mio: -1
	mio: -2147483647
	mio: 0
	mio: 13232
	mio: 13232
	mio: -13232
	mio: -42

[Indice](#indice)

## camel_to_snake
<details>
<summary>subject</summary>

	Assignment name  : camel_to_snake
	Expected files   : camel_to_snake.c
	Allowed functions: malloc, free, realloc, write
	--------------------------------------------------------------------------------

	Write a program that takes a single string in lowerCamelCase format
	and converts it into a string in snake_case format.

	A lowerCamelCase string is a string where each word begins with a capital letter
	except for the first one.

	A snake_case string is a string where each word is in lower case, separated by
	an underscore "_".

	Examples:
	$>./camel_to_snake "hereIsACamelCaseWord"
	here_is_a_camel_case_word
	$>./camel_to_snake "helloWorld" | cat -e
	hello_world$
	$>./camel_to_snake | cat -e
	$

</details>

```c
 #include <unistd.h>

int	main(int n, char **str)
{
	if(n == 2)
	{
		int i = 0;
		while(str[1][i] != '\0')
		{
			if(str[1][i] >= 'A' && str[1][i] <= 'Z')
			{
				write(1, "_", 1);
				str[1][i] += 32;
			}
			write(1, &str[1][i], 1);
			i++;
		}
	}
	return(0);
}
```

[Indice](#indice)

## do_op
<details>
<summary>subject</summary>

	Assignment name  : do_op
	Expected files   : *.c, *.h
	Allowed functions: atoi, printf, write
	--------------------------------------------------------------------------------

	Write a program that takes three strings:
	- The first and the third one are representations of base-10 signed integers
		that fit in an int.
	- The second one is an arithmetic operator chosen from: + - * / %

	The program must display the result of the requested arithmetic operation,
	followed by a newline. If the number of parameters is not 3, the program
	just displays a newline.

	You can assume the string have no mistakes or extraneous characters. Negative
	numbers, in input or output, will have one and only one leading '-'. The
	result of the operation fits in an int.

	Examples:

	$> ./do_op "123" "*" 456 | cat -e
	56088$
	$> ./do_op "9828" "/" 234 | cat -e
	42$
	$> ./do_op "1" "+" "-43" | cat -e
	-42$
	$> ./do_op | cat -e
	$

</details>

```c
 #include <stdlib.h>
 #include <stdio.h>

int	main(int n, char **str)
{
	if(n == 4)
	{
		int uno = atoi(str[1]);
		int dos = atoi(str[3]);

		if(str[2][0] == '+')
			printf("%i", uno + dos);
		if(str[2][0] == '-')
			printf("%i", uno - dos);
		if(str[2][0] == '*')
			printf("%i", uno * dos);
		if(str[2][0] == '/')
			printf("%i", uno / dos);
		if(str[2][0] == '%')
			printf("%i", uno % dos);
	}
	printf("\n");
}
```

[Indice](#indice)

## ft_strcspn

<details>
<summary>subject</summary>

	Assignment name  : ft_strcspn
	Expected files   : ft_strcspn.c
	Allowed functions: 
	--------------------------------------------------------------------------------

	Reproduce the behavior of the function strcspn (man strcspn).

	Your function must be declared as follows:

	size_t  ft_strcspn(const char   *s, const char  *reject);

</details>


```c
size_t	ft_strcspn(const char *s, const char *reject)
{
	int i = 0;
	int j = 0;

	while(reject[i])
	{
		while(s[j])
		{
			if(s[j] == reject[i])
				return j;
			j++;
		}
		i++;
	}
	return(j);
}
```
```c
#include <stdio.h>
#include <string.h>

int	main(void)
{
	char aa[] = "test";
	char bb[] = "f";

	printf("mio: %lu\n", ft_strcspn(aa, bb));
	printf("ori: %lu\n", strcspn(aa, bb));
}
```
	mio: 4
	ori: 4

[Indice](#indice)

## ft_strdup

<details>
<summary>subject</summary>

	Assignment name  : ft_strdup
	Expected files   : ft_strdup.c
	Allowed functions: malloc
	--------------------------------------------------------------------------------

	Reproduce the behavior of the function strdup (man strdup).

	Your function must be declared as follows:

	char    *ft_strdup(char *src);

</details>


```c
#include <stdlib.h>

char	*ft_strdup(char *src)
{
	int i = 0;
	char *res;

	while(src[i])
		i++;
	res = malloc(i + 1);
	if(!res)
		return(NULL);
	i = 0;
	while(src[i])
	{
		res[i] = src[i];
		i++;
	}
	res[i] = '\0';

	return(res);
}
```
```c
#include <stdio.h>

int	main(void)
{
	char *cp;

	cp = ft_strdup("copiado");

	printf("%s", cp);

}
```

[Indice](#indice)

## ft_strpbrk
<details>
<summary>subject</summary>

	Assignment name	: ft_strpbrk
	Expected files	: ft_strpbrk.c
	Allowed functions: None
	---------------------------------------------------------------

	Reproduce exactly the behavior of the function strpbrk
	(man strpbrk).

	The function should be prototyped as follows:

	char	*ft_strpbrk(const char *s1, const char *s2);

</details>

```c
char	*ft_strpbrk(const char *s1, const char *s2)
{
	int	i;

	while(s1)
	{
		i = 0;
		while(s2[i])
		{
			if(*s1 == s2[i])
				return((char*)s1);
			i++;
		}
		s1++;
	}
	return(0);
}
```
```c
#include <string.h>
#include <stdio.h>

int	main(void)
{
	const char s[] = "AADff";
	const char c[] = "dfASiCd";

	printf("ori: %s\n", strpbrk(s, c));
	printf("mio: %s\n", ft_strpbrk(s, c));
}
```
	ori: AADff
	mio: AADff

[Indice](#indice)

## ft_strrev
<details>
<summary>subject</summary>

	Assignment name  : ft_strrev
	Expected files   : ft_strrev.c
	Allowed functions: 
	--------------------------------------------------------------------------------

	Write a function that reverses (in-place) a string.

	It must return its parameter.

	Your function must be declared as follows:

	char    *ft_strrev(char *str);

</details>

```c
char *ft_strrev(char *str)
{
	int len = 0;
	int i = 0;
	char tmp = 0;

	while (str[len])
		len++;
	len--;
	while (i < len)
	{
		tmp = str[len];
		str[len] = str[i];
		str[i] = tmp;
		i++;
		len--;
	}
	return (str);
}
```
```c
#include <stdio.h>
int main(void)
{
	char s[] = "Hello World";
	ft_strrev(s);
	printf("%s\n", s);
	return (0);
}
```

[Indice](#indice)

## ft_strspn
<details>
<summary>subject</summary>

	Assignment name	: ft_strspn
	Expected files	: ft_strspn.c
	Allowed functions: None
	---------------------------------------------------------------

	Reproduce exactly the behavior of the strspn function 
	(man strspn).

	The function should be prototyped as follows:

	size_t	ft_strspn(const char *s, const char *accept);

</details>

```c
size_t	ft_strspn(const char *s, const char *accept)
{
	const char *t_s = s;
	const char *t_a;

	while(*t_s)
	{
		t_a = accept;
		while(1)
		{
			if(*t_s == *t_a)
				break;
			else if (*t_a++ == '\0')
				return(t_s - s);
		}
		t_s++;
	}
	return(t_s - s);
}
```
```c
#include <string.h>
#include <stdio.h>

int	main(void)
{
	char s[] = "ABABC";
	char a[] = "ACB";

	printf("ori: %lu \n", strspn(s, a));
	printf("mio: %lu \n", ft_strspn(s, a));
	return(0);
}
```

[Indice](#indice)

## is_power_of_2
<details>
<summary>subject</summary>

	Assignment name  : is_power_of_2
	Expected files   : is_power_of_2.c
	Allowed functions: None
	--------------------------------------------------------------------------------

	Write a function that determines if a given number is a power of 2.

	This function returns 1 if the given number is a power of 2, otherwise it returns 0.

	Your function must be declared as follows:

	int	    is_power_of_2(unsigned int n);

	--------------------------------------------------------------------------------

	#include <stdio.h>
	int main()
	{
		int	n;

		printf("%d\n", is_power_of_2(64));
	}

</details>

```c
int	is_power_of_2(unsigned int n)
{
	if(n == 0)
		return(0);
	else if (n == 1 || n % 2 == 0)
		return(1);
	else
	return(0);
}
```
```c
#include <stdio.h>
#include <stdlib.h>

int main(int n, char **str)
{
	unsigned int num = atoi(str[1]);

	printf("es %d\n", is_power_of_2(num));
	
}
```

[Indice](#indice)

## last_word
<details>
<summary>subject</summary>

	Assignment name  : last_word
	Expected files   : i
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays its last word followed by a \n.

	A word is a section of string delimited by spaces/tabs or by the start/end of
	the string.

	If the number of parameters is not 1, or there are no words, display a newline.

	Example:

	$> ./last_word "FOR PONY" | cat -e
	PONY$
	$> ./last_word "this        ...       is sparta, then again, maybe    not" | cat -e
	not$
	$> ./last_word "   " | cat -e
	$
	$> ./last_word "a" "b" | cat -e
	$
	$> ./last_word "  lorem,ipsum  " | cat -e
	lorem,ipsum$
	$>

</details>

```c
#include <unistd.h>

int	main(int n, char **str)
{
	if(n == 2)
	{
		int i = 0;
		while (str[1][i])
			i++;
		i--;
		while (str[1][i] == ' ' || str[1][i] == '\t')
			i--;
		while (str[1][i] >= '!' && str[1][i] <= '~')
			i--;
		i++;
		while (str[1][i] >= '!' && str[1][i] <= '~')
		{
			write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
}
```

[Indice](#indice)

## max

<details>
<summary>subject</summary>

	Assignment name  : max
	Expected files   : max.c
	Allowed functions: 
	--------------------------------------------------------------------------------

	Write the following function:

	int		max(int* tab, unsigned int len);

	The first parameter is an array of int, the second is the number of elements in
	the array.

	The function returns the largest number found in the array.

	If the array is empty, the function returns 0.

</details>

```c
int	max(int* tab, unsigned int len)
{
	int i = 0;
	if(!len)
		return(0);
	while(i < len)
	{
		if(tab[0] < tab[i])
			tab[0] = tab[i];
		i++;
	}
	return(tab[0]);
}
```
```c
#include <stdio.h>

int main(void)
{
	int arr[8] = {7, -42, 0, 58, -64, -2, -68, -1};
	int res = max(arr, 8);
	
	printf("max: %d\n", res);
	return(0);
}
```

[Indice](#indice)

## print_bits
<details>
<summary>subject</summary>

	Assignment name  : print_bits
	Expected files   : print_bits.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a function that takes a byte, and prints it in binary WITHOUT A NEWLINE
	AT THE END.

	Your function must be declared as follows:

	void	print_bits(unsigned char octet);

	Example, if you pass 2 to print_bits, it will print "00000010"

</details>

```c
#include <unistd.h>

void	print_bits(unsigned char octet)
{
	int i = 7;
	char bits;

	while(i >= 0)
	{
		bits = ((octet >> i) & 1) + '0';
		write(1, &bits, 1);
		i--;
	}

}
```

[Indice](#indice)

## snake_to_camel

<details>
<summary>subject</summary>

	Assignment name  : snake_to_camel
	Expected files   : snake_to_camel.c
	Allowed functions: malloc, free, realloc, write
	--------------------------------------------------------------------------------

	Write a program that takes a single string in snake_case format
	and converts it into a string in lowerCamelCase format.

	A snake_case string is a string where each word is in lower case, separated by
	an underscore "_".

	A lowerCamelCase string is a string where each word begins with a capital letter
	except for the first one.

	Examples:
	$>./camel_to_snake "here_is_a_snake_case_word"
	hereIsASnakeCaseWord
	$>./camel_to_snake "hello_world" | cat -e
	helloWorld$
	$>./camel_to_snake | cat -e
	$

</details>

```c
int	main(int n, char **str)
{
	if(n == 2)
	{
		int i = 0;
		while(str[1][i])
		{
			if(str[1][i] == '_')
				i++;
			if(str[1][i - 1] == '_')
				str[1][i] -= 32;
			write(1, &str[1][i], 1);
			i++;
		}
	}
	write(1, "\n", 1);
	return (0);
}
```

[Indice](#indice)

## strcmp
<details>
<summary>subject</summary>

	Assignment name  : ft_strcmp
	Expected files   : ft_strcmp.c
	Allowed functions:
	--------------------------------------------------------------------------------

	Reproduce the behavior of the function strcmp (man strcmp).

	Your function must be declared as follows:

	int    ft_strcmp(char *s1, char *s2);

</details>

```c
int	ft_strcmp(char  *s1, char   *s2)
{
	int i = 0;
	while (s1[i] && s2[i] && s1[i] == s2[i])
		i++;
	return (s1[i] - s2[i]);
}
```
```c
int	main(void)
{

	char a[] = "a";
	char b[] = "ievbwvbew";

	printf("mio: %d\n", ft_strcmp(a,b));
	printf("original: %d\n", strcmp(a,b));

}
```

[Indice](#indice)

## swap_bits
<details>
<summary>subject</summary>

	Assignment name  : swap_bits
	Expected files   : swap_bits.c
	Allowed functions:
	--------------------------------------------------------------------------------

	Write a function that takes a byte, swaps its halves (like the example) and
	returns the result.

	Your function must be declared as follows:

	unsigned char	swap_bits(unsigned char octet);

	Example:

		1 byte
	_____________
	0100 | 0001
	    \ /
	    / \
	0001 | 0100

	0011 1110

</details>

```c
unsigned char	swap_bits(unsigned char octet)
{
	return((octet >> 4) | (octet << 4));
}
```

[Indice](#indice)

## union

<details>
<summary>subject</summary>

	Assignment name  : union
	Expected files   : union.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes two strings and displays, without doubles, the
	characters that appear in either one of the strings.

	The display will be in the order characters appear in the command line, and
	will be followed by a \n.

	If the number of arguments is not 2, the program displays \n.

	Example:

	$>./union zpadinton "paqefwtdjetyiytjneytjoeyjnejeyj" | cat -e
	zpadintoqefwjy$
	$>./union ddf6vewg64f gtwthgdwthdwfteewhrtag6h4ffdhsd | cat -e
	df6vewg4thras$
	$>./union "rien" "cette phrase ne cache rien" | cat -e
	rienct phas$
	$>./union | cat -e
	$
	$>
	$>./union "rien" | cat -e
	$
	$>

</details>

```c
#include <unistd.h>

int main(int n, char **str)
{
	if (n == 3)
	{
		int i = 1;
		int arr[255] = {0};

		while (i <= 2)
		{
			int j = 0;
			while (str[i][j])
			{
				if (!arr[(int)str[i][j]])
				{
					write(1, &str[i][j], 1);
					arr[(int)str[i][j]] = 1;
				}
				j++;
			}
			i++;
		}
	}
	write(1, "\n", 1);
	return (0);
}
```

[Indice](#indice)

# Level 2

-------------
<details>
<summary>subject</summary>

</details>

[Indice](#indice)