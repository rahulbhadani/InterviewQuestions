# Reverse a string

```{c++}
#include<iostream>
#include<vector>
using namespace std;


void string_reverse(char* strng, int sz)// Two arguments: string, and length of the string
{
    char* new_string;
    new_string = (char*)malloc(sz);

    int i = 0;
    while(strng[i]!='\0')
    {
        printf("%d", i);
        new_string[sz - i - 1] = strng[i];
        i++;
    }
    new_string[sz - 1] = '\0';
    printf("%s", new_string);
    return;
}

int main()
{
    char test[5] = "elep";
    string_reverse(test, 5);
	return 0;
}
```
