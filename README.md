
## Índice
Level 0
- [ft_putstr](#ft_putstr)
- [ft_strlen](#ft_strlen)
- [rev_print](#rev_print)
- [first_word](#first_word)
- [fizzbuzz](#fizzbuzz)
- [ft_strcpy](#ft_strcpy)
- [ft_swap](#ft_swap)
- [repeat_alpha](#repeat_alpha)
- [rot_13](#rot_13)


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

## rev_print

<details>
<summary>subject</summary>

	Assignment name  : rev_print
	Expected files   : rev_print.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string, and displays the string in reverse
	followed by a newline.

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
## first_word
<details>
<summary>subject</summary>

	Assignment name  : first_word
	Expected files   : first_word.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays its first word, followed by a
	newline.

	A word is a section of string delimited by spaces/tabs or by the start/end of
	the string.

	If the number of parameters is not 1, or if there are no words, simply display
	a newline.

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
## fizzbuzz
<details>
<summary>subject</summary>

	Assignment name  : fizzbuzz
	Expected files   : fizzbuzz.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that prints the numbers from 1 to 100, each separated by a
	newline.

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
## ft_strcpy
<details>
<summary>subject</summary>

	Assignment name  : first_word
	Expected files   : first_word.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays its first word, followed by a
	newline.

	A word is a section of string delimited by spaces/tabs or by the start/end of
	the string.

	If the number of parameters is not 1, or if there are no words, simply display
	a newline.

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
## fizzbuzz
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

## ft_swap
<details>
<summary>subject</summary>

	Assignment name  : ft_swap
	Expected files   : ft_swap.c
	Allowed functions: 
	--------------------------------------------------------------------------------

	Write a function that swaps the contents of two integers the adresses of which
	are passed as parameters.

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

## repeat_alpha
<details>
<summary>subject</summary>

	Assignment name  : repeat_alpha
	Expected files   : repeat_alpha.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program called repeat_alpha that takes a string and display it
	repeating each alphabetical character as many times as its alphabetical index,
	followed by a newline.

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

## rot_13

<details>
<summary>subject</summary>

	Assignment name  : rot_13
	Expected files   : rot_13.c
	Allowed functions: write
	--------------------------------------------------------------------------------

	Write a program that takes a string and displays it, replacing each of its
	letters by the letter 13 spaces ahead in alphabetical order.

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

-------------
<details>
<summary>subject</summary>


</details>