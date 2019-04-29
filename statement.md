# What does the memory of a process looks like ?

The code snippet below is a simple program that declares a bunch of elements, before displaying their adresses in memory.

```C runnable
#include <stdio.h>
#include <stdlib.h>

void f(){NULL;}
int global = 0;

int main(){
  int* p = malloc(3*sizeof(int));
  *p = 1;
  *(p+3) = 3;
  printf("Value pointed by p: 		%d\n",*p);
  printf("Address pointed by p: 	%p\n", p);
  printf("Address of p: 					%p\n",&p);
  printf("Value pointed by p+3: 	%d\n",*(p+3));
  printf("Address pointed by p+3:	%p\n", (p+3));
  printf("Address of function f : %p\n", f);
	printf("Address of main : %p\n", main);
  printf("Address of global var : %p\n",&global);
}
```

Some remarks:
- **Contiguous allocation**: You can notice that the addresses of p and (p+3) are separated by an actual offset of 3. The `malloc` function allocates contiguous memory, all the addresses are one after the other.
- **Zones**: The values of the addresses may change from one execution to the other. However, you may notice that some addresses are closer to each other. Try to add another function, or another local variable, and see how the addresses are grouped.
