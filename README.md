# Pi
Thousand decimals of Pi using The GNU Multiple Precision Arithmetic Library

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


```
3.141592653589793238462643383279502884197169399375105820974944592307816406286208998628034825342117067982148086513282306647093844609550582231725359408128481117450284102701938521105559644622948954930381964428810975665933446128475648233786783165271201909145648566923460348610454326648213393607260249141273724587006606315588174881520920962829254091715364367892590360011330530548820466521384146951941511609433057270365759591953092186117381932611793105118548074462379962749567351885752724891227938183011949129833673362440656643086021394946395224737190702179860943702770539217176293176752384674818467669405132000568127145263560827785771342757789609173637178721468440901224953430146549585371050792279689258923542019956112129021960864034418159813629774771309960518707211349999998372978049951059731732816096318595024459455346908302642522308253344685035261931188171010003137838752886587533208381420617177669147303598253490428755468731159562863882353787593751957781857780532171226806613001927876611195909216420199
```
