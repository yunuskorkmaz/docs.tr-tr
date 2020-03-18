---
title: Dallar ve döngüler - C# eğitimine giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri tekrar tekrar yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini keşfetmek için C# kodu yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73739131"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dal ve döngü deyimleri ile koşullu mantığı öğrenin

Bu öğretici, değişkenleri inceleyen ve bu değişkenleri temel alan yürütme yolunu değiştiren kod yazmayı öğretir. C# kodu yazar sınız ve derleme ve çalıştırma sonuçlarını görürsünüz. Öğretici C# dallanma ve döngü yapıları keşfetmek ders bir dizi içerir. Bu dersler size C# dilinin temel özelliklerini öğretir.

Bu öğretici, geliştirme için kullanabileceğiniz bir makineye sahip olmak için bekliyor. .NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir. Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md) dır.

## <a name="make-decisions-using-the-if-statement"></a>İfadeyi kullanarak `if` kararlar verme

*Dallar-öğretici*adlı bir dizin oluşturun. Geçerli dizinini yapın ve aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide *Program.cs* açın `Console.WriteLine("Hello World!");` ve satırı aşağıdaki kodla değiştirin:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Konsol pencerenize `dotnet run` yazarak bu kodu deneyin. "Yanıt 10'dan büyüktür" iletisini görmelisiniz. konsolunuza yazdırılır.

`b` tanımlamasını toplamın 10’dan küçük olacağı şekilde değiştirin:

```csharp
int b = 3;
```

Tekrar `dotnet run` yazın. Yanıt 10’dan küçük olduğundan herhangi bir şey yazdırılmaz. Test ettiğiniz **koşul** false değerindedir. Bir `if` deyimi için olası dallardan yalnızca birini (true dalı) yazdığınızdan, yürütülecek herhangi bir kodunuz yoktur.

> [!TIP]
> C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. Derleyici hataları bulur ve bildirir. Hata çıktısını ve hatayı oluşturan kodu yakından incegörün. Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.

Bu ilk örnek ve `if` Boolean türlerinin gücünü gösterir. *Boolean* iki değerden birine sahip olabilecek `true` bir `false`değişkendir: veya . C# Boolean `bool` değişkenleri için özel bir tür tanımlar. `if` deyimi bir `bool` için değeri kontrol eder. Değer `true` olduğunda, `if` deyiminden sonra gelen deyim yürütülür. Aksi halde atlanır.

Koşulları kontrol etmek ve bu koşullara göre deyimleri yürütmek için gerçekleştirilen bu işlem son derece etkilidir.

## <a name="make-if-and-else-work-together"></a>if ve else koşullarını birlikte çalıştırma

Hem true hem de false dallarında farklı kod yürütmek için, koşul false olduğunda yürütülen bir `else` dalı oluşturursunuz. Bunu dene. Aşağıdaki koddaki son iki satırı `Main` yönteminize ekleyin (ilk dördüne zaten sahip olmalısınız):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

`else` anahtar sözcüğünden sonraki deyim, yalnızca test edilen koşul `false` olduğunda yürütülür. Boolean `if` `else` koşullarını birleştirerek hem bir hem de bir `true` `false` durumu işlemek için ihtiyacınız olan tüm gücü sağlar.

> [!IMPORTANT]
> `if` ve `else` deyimlerinin altındaki girinti, insan okuyuculara yöneliktir.
> C# dili girinti veya beyaz boşluk önemli olarak tedavi etmez.
> `if` veya `else` anahtar sözcüğünden sonra gelen deyim, koşula bağlı olarak yürütülür. Bu öğreticideki tüm örnekler, deyimlerin denetim akışına dayalı girintisi satırlara yönelik yaygın bir uygulamayı izler.

Girinti dikkate alınmadığından, koşullu olarak yürütülen bloğun birden çok deyim içermesini istediğinizde bunu belirtmek için `{` ve `}` ayraçlarını kullanmanız gerekir. C# programcıları bu ayraçları genellikle tüm `if` and `else` tümcelerinde kullanır. Aşağıdaki örnek, az önce oluşturduğunuz örnekle aynıdır. Yukarıdaki kodunuzu aşağıdaki kodla eşleşecek şekilde değiştirin:

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> Bu öğreticinin geri kalanı boyunca, kod örneklerinin tümü, kabul edilen uygulamaları izleyerek parantezleri içerir.

Daha karmaşık koşulları test edebilirsiniz. Şimdiye kadar yazdığınız `Main` koddan sonra yönteminize aşağıdaki kodu ekleyin:

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

Eşitlik `==` *için*sembol testleri. Kullanmak, `==` eşitlik için testi atamadan ayırır, `a = 5`bunu ' da gördüğünüz.

`&&` "ve" sözcüğünü ifade eder. Bu, deyimi true dalında yürütmek için her iki koşulun da true olması gerektiği anlamına gelir.  Bu örnekler aynı zamanda, `{` ve `}` ayraçları içine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip olabileceğinizi de gösterir.

"veya" `||` temsil etmek için de kullanabilirsiniz. Şimdiye kadar yazdıkların ardından aşağıdaki kodu ekleyin:

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

`a`, `b`ve `c` , ve arasında `&&` geçiş `||` ve keşfetmek için değerlerini değiştirin. Operatörlerin ve `&&` `||` operatörlerin nasıl çalıştığını daha iyi anlayasınız.

İlk adımı bitirdin. Bir sonraki bölümü başlatmadan önce, geçerli kodu ayrı bir yönteme taşıyalım. Bu, yeni bir örnekle çalışmaya başlamayı kolaylaştırır. Metodunuzu `ExploreIf` yeniden adlandırın `Main` `Main` ve `ExploreIf`çağıran yeni bir yöntem yazın. Bitirdikten sonra, kodunuz şu şekilde görünmelidir:

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

Çağrıyı yorumla. `ExploreIf()` Bu bölümde çalışırken çıktıdaha az darmadağın yapacaktır:

```csharp
//ExploreIf();
```

C#'da `//` bir **yorum** başlar. Yorumlar, kaynak kodunuzda tutmak istediğiniz ancak kod olarak yürütülmemek istemediğiniz herhangi bir metindir. Derleyici yorumlardan yürütülebilir bir kod oluşturmaz.

## <a name="use-loops-to-repeat-operations"></a>İşlemleri yinelemek için döngüleri kullanma

Bu bölümde ifadeleri yinelemek için **döngüler** kullanın. Yönteminizde `Main` bu kodu deneyin:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

İfade `while` bir koşulu denetler ve aşağıdaki ifade `while`veya deyim bloğunu yürütür. Bu durum tekrar tekrar denetler ve koşul yanlış olana kadar bu ifadeleri yürütme.

Bu örnekte diğer bir yeni işleç mevcuttur. `counter` değişkeninden sonra gelen `++`, **artırma** işlecidir. Bu değere 1 `counter` ekler ve `counter` değişkende bu değeri depolar.

> [!IMPORTANT]
> Kodu çalıştırırken `while` döngü koşulunun false olarak değiştiğinden emin olun. Aksi halde, programınızın hiç sona ermediği **sonsuz bir döngü** oluşturmuş olursunuz. Bu örnekte gösterilmiş değildir, çünkü programınızı **CTRL-C** veya başka yolla kullanmayı bırakmaya zorlamanız gerekir.

`while` döngüsü, `while` koşulundan sonraki kodu yürütmeden önce koşulu test eder. `do` ... `while` döngüsü önce kodu yürütür, sonra koşulu kontrol eder. Do while döngüsü aşağıdaki kodda gösterilir:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Bu `do` döngü ve `while` önceki döngü aynı çıktıyı üretir.

## <a name="work-with-the-for-loop"></a>For döngüsü ile çalışma

**For** döngüsü genellikle C#'da kullanılır. Main() yönteminizde bu kodu deneyin:

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Bu, `while` döngüsü ve zaten kullandığınız `do` döngüsü ile aynı işlevi görür. `for` deyiminde, bunu nasıl çalıştığını denetleyen üç bölüm bulunur.

İlk bölüm **için başharf**: `int index = 0;` döngü `index` değişkeni olduğunu bildirir ve ilk `0`değerini ayarlar.

Orta kısım **for koşuldur**: `index < 10` sayacın değeri 10'dan küçük olduğu sürece bu `for` döngünün yürütmeye devam ettiğini bildirir.

Son bölüm **iterator için** `index++` : `for` deyimi izleyen blok çalıştırdıktan sonra döngü değişkeninin nasıl değiştirilebildiğini belirtir. Bu bölüm, bloğun her yürütme işleminde `index` değişkeninin 1 artırılması gerektiğini belirtir.

Bunları kendiniz deneyin. Aşağıdakilerden her birini deneyin:

- Farklı bir değerde başlamak için başlatıcıyı değiştirin.
- Farklı bir değerde durmak için koşulu değiştirin.

İşiniz bittiğinde öğrendiklerinizi kullanmak için kendi kendinize kod yazma adımına geçelim.

## <a name="combine-branches-and-loops"></a>Dalları ve döngüleri birleştirme

C# dilinde `if` deyimini ve döngü yapılarını gördüğünüze göre şimdi 1 ile 20 arasında olup 3’e bölünebilen tüm tamsayıların toplamını bulmak için C# kodu yazmayı deneyin.  Aşağıdaki ipuçlarından yararlanabilirsiniz:

- `%` işleci size bölme işlemindeki kalanı verir.
- `if` deyimi bir sayının toplama dahil edilip edilmemesi gerektiğini görmeniz için size koşulu verir.
- `for` döngüsü 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olur.

Kendiniz deneyin. Daha sonra başarılı olup olmadığınıza bakın. Cevap için 63 almalısın. [Tamamlanmış kodu GitHub'da görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıtı görebilirsiniz.

"Dallar ve döngüler" eğitimini tamamladınız.

Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğretici ile devam edebilirsiniz.

Aşağıdaki konulardan bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:

- [If ve else deyimi](../../language-reference/keywords/if-else.md)
- [İfade iken](../../language-reference/keywords/while.md)
- [Do deyimi](../../language-reference/keywords/do.md)
- [İfade için](../../language-reference/keywords/for.md)
