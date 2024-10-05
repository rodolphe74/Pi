# Pi
Thousand decimals of Pi using The GNU Multiple PrecisionArithmetic Library

```C++
#include <iostream>
#include <gmpxx.h>
#include <gmp.h>

#define MAXF 1000
#define PREC 4096

int main()
{
    std::cout << "Bailey-Borwein-Plouffe" << std::endl;

    mpf_set_default_prec(PREC);
    std::cout.precision(MAXF);

    mpf_class m, l;
    mpf_t p, a;
    mpf_init2(a, PREC);
    mpf_init2(p, PREC);
    mpf_set_d(a, 0.0625);
    m = 0;

    for (unsigned long i = 0; i < MAXF; i++) {
        l = 8 * i;
        mpf_pow_ui(p, a, i);
        mpf_class q(p);
        m += ((4 / (l + 1) - 2 / (l + 4) - 1 / (l + 5) - 1 / (l + 6)) * q);
    }

    std::cout << m << std::endl;

    mpf_clear(a);
    mpf_clear(p);
}
```
