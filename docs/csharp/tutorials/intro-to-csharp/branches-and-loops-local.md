---
title: Dallar ve döngüler-C# öğreticisine giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere C# kodu yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396875"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dal ve döngü deyimleri ile koşullu mantık öğrenin

Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir. C# kodu yazar ve bunu derleyip çalıştırmanın sonuçlarını görürsünüz. Öğretici, C# ' de dallanma ve döngü yapılarını keşfetmenizi sağlayan bir dizi ders içerir. Bu dersler size C# dilinin temel özelliklerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="make-decisions-using-the-if-statement"></a>İfadesini kullanarak kararlar alın `if`

Dallar adlı bir dizin oluşturun *-öğretici*. Geçerli dizini yapın ve şu komutu çalıştırın:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide *program.cs* açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Konsol pencerenizi yazarak bu kodu deneyin `dotnet run` . "Yanıt 10 ' dan büyük" iletisini görmeniz gerekir. konsolunuza yazdırılır.

`b` tanımlamasını toplamın 10’dan küçük olacağı şekilde değiştirin:

```csharp
int b = 3;
```

`dotnet run`Yeniden yazın. Yanıt 10’dan küçük olduğundan herhangi bir şey yazdırılmaz. Test ettiğiniz **koşul** false değerindedir. Bir `if` deyimi için olası dallardan yalnızca birini (true dalı) yazdığınızdan, yürütülecek herhangi bir kodunuz yoktur.

> [!TIP]
> C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. Derleyici hataları bulacak ve rapor eder. Hata çıktısına ve hatayı oluşturan koda yakından bakın. Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.

Bu ilk örnek, `if` ve Boolean türlerin gücünü gösterir. *Boolean* , iki değerden birine sahip olabilir bir değişkendir: `true` veya `false` . C#, Boole değişkenleri için özel bir tür tanımlar `bool` . `if` deyimi bir `bool` için değeri kontrol eder. Değer `true` olduğunda, `if` deyiminden sonra gelen deyim yürütülür. Aksi takdirde, atlanır.

Bu koşullara göre koşulları denetleme ve deyimleri yürütme işlemi güçlü bir işlemdir.

## <a name="make-if-and-else-work-together"></a>if ve else koşullarını birlikte çalıştırma

Hem true hem de false dallarında farklı kod yürütmek için, koşul false olduğunda yürütülen bir `else` dalı oluşturursunuz. Bunu deneyin. Aşağıdaki kodda bulunan son iki satırı `Main` yöntemine ekleyin (ilk dördü zaten var olmalıdır):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

`else` anahtar sözcüğünden sonraki deyim, yalnızca test edilen koşul `false` olduğunda yürütülür. `if`Ve `else` Boolean koşulları ile birleştirmek, hem hem de bir koşulu işlemek için ihtiyacınız olan tüm gücü sağlar `true` `false` .

> [!IMPORTANT]
> `if` ve `else` deyimlerinin altındaki girinti, insan okuyuculara yöneliktir.
> C# dili, girintileme veya boşluk olarak kabul etmez.
> `if` veya `else` anahtar sözcüğünden sonra gelen deyim, koşula bağlı olarak yürütülür. Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.

Girintileme önemli olmadığından, `{` `}` çok sayıda deyimin koşullu olarak yürütülen bloğun bir parçası olmasını istediğiniz zaman göstermek için ve kullanmanız gerekir. C# programcıları bu ayraçları genellikle tüm `if` and `else` tümcelerinde kullanır. Aşağıdaki örnek, oluşturduğunuz bir ile aynıdır. Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:

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
> Bu öğreticinin geri kalanında, kod örnekleri, kabul edilen uygulamaları takip eden ayraçları içerir.

Daha karmaşık koşulları test edebilirsiniz. Şu `Main` ana kadar yazdığınız koddan sonra aşağıdaki kodu yöntemine ekleyin:

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

`==` *Eşitlik*için simge testi. `==`' Yi kullanarak, ' de gördüğünüz şekilde testi, atamanın eşitliğine ayırır `a = 5` .

`&&` "ve" sözcüğünü ifade eder. Bu, deyimi true dalında yürütmek için her iki koşulun da true olması gerektiği anlamına gelir.  Bu örnekler aynı zamanda, `{` ve `}` ayraçları içine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip olabileceğinizi de gösterir.

`||`"Veya" öğesini göstermek için de kullanabilirsiniz. Şu ana kadar yazıldıktan sonra aşağıdaki kodu ekleyin:

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

, Ve değerlerini değiştirin `a` ve `b` `c` arasında geçiş yapın `&&` `||` . Ve işleçlerinin nasıl çalıştığını daha fazla anlayacaksınız `&&` `||` .

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. `Main`Yönteminizi olarak yeniden adlandırın `ExploreIf` ve çağıran yeni bir `Main` Yöntem yazın `ExploreIf` . İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:

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

Çağrısını not edin `ExploreIf()` . Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//ExploreIf();
```

`//`C# dilinde bir **Açıklama** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

## <a name="use-loops-to-repeat-operations"></a>İşlemleri yinelemek için döngüleri kullanma

Bu bölümde, deyimlerini yinelemek için **döngüleri** kullanırsınız. Bu kodu yönteminizin içinde deneyin `Main` :

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while`İfade bir koşulu denetler ve öğesinden sonra deyimin veya bildiri bloğunu yürütür `while` . Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.

Bu örnekte diğer bir yeni işleç mevcuttur. `counter` değişkeninden sonra gelen `++`, **artırma** işlecidir. Değerine 1 ekler `counter` ve bu değeri `counter` değişkende depolar.

> [!IMPORTANT]
> `while`Kodu yürüttüğünüzde döngü koşulunun yanlış olarak değiştiği emin olun. Aksi halde, programınızın hiç sona ermediği **sonsuz bir döngü** oluşturmuş olursunuz. Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.

`while` döngüsü, `while` koşulundan sonraki kodu yürütmeden önce koşulu test eder. `do` ... `while` döngüsü önce kodu yürütür, sonra koşulu kontrol eder. *Do while* döngüsü aşağıdaki kodda gösterilmiştir:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Bu `do` döngü ve önceki `while` döngü aynı çıktıyı üretir.

## <a name="work-with-the-for-loop"></a>For döngüsü ile çalışma

**For** döngüsü genellikle C# dilinde kullanılır. Main () yönteminde bu kodu deneyin:

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Önceki kod, `while` döngüyle aynı çalışmayı ve `do` zaten kullandığınız döngüyü yapar. `for` deyiminde, bunu nasıl çalıştığını denetleyen üç bölüm bulunur.

İlk bölüm **for başlatıcıdır**: `int index = 0;` Loop değişkeni olduğunu bildirir `index` ve başlangıç değerini olarak ayarlar `0` .

Orta kısım **for koşuludur**: `index < 10` `for` sayacın değeri 10 ' dan az olduğu sürece bu döngünün yürütülmeye devam ettiğini bildirir.

Son bölüm, **Yineleyici için**: `index++` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir `for` . Bu bölüm, bloğun her yürütme işleminde `index` değişkeninin 1 artırılması gerektiğini belirtir.

Kendiniz deneyin. Aşağıdaki çeşitlemelerin her birini deneyin:

- Farklı bir değerde başlamak için başlatıcıyı değiştirin.
- Farklı bir değerde durmak için koşulu değiştirin.

İşiniz bittiğinde öğrendiklerinizi kullanmak için kendi kendinize kod yazma adımına geçelim.

Bu öğreticide kapsanmayan başka bir döngü bildirisi vardır: `foreach` ifade. `foreach`İfade, öğe dizisindeki her öğe için kendi ifadesini yineler. En sık *koleksiyonlarla*birlikte kullanılır, bu nedenle sonraki öğreticide ele alınmıştır.

## <a name="created-nested-loops"></a>İç içe geçmiş döngüler oluşturuldu

Bir `while` , `do` veya `for` döngüsü, iç döngüde her öğe ile dış döngüdeki her bir öğenin birleşimini kullanarak bir matris oluşturmak için başka bir döngünün içinde iç içe olabilir. Satırları ve sütunları temsil etmek için alfasayısal çiftler kümesi oluşturmayı görelim.

Bir `for` döngü satırları oluşturabilir:

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

Şu sütunları başka bir döngü oluşturabilir:

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

Bir döngüyü diğerinin içine, çiftler halinde iç içe geçirebilirsiniz:

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

İç döngünün her tam çalışması için dış döngünün bir kez artıyor olduğunu görebilirsiniz. Satır ve sütun iç içe geçirmeyi tersine çevirin ve yaptığınız değişiklikleri kendiniz görün.

## <a name="combine-branches-and-loops"></a>Dalları ve döngüleri birleştirme

C# dilinde `if` deyimini ve döngü yapılarını gördüğünüze göre şimdi 1 ile 20 arasında olup 3’e bölünebilen tüm tamsayıların toplamını bulmak için C# kodu yazmayı deneyin.  Aşağıdaki ipuçlarından yararlanabilirsiniz:

- `%` işleci size bölme işlemindeki kalanı verir.
- `if` deyimi bir sayının toplama dahil edilip edilmemesi gerektiğini görmeniz için size koşulu verir.
- `for` döngüsü 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olur.

Kendiniz deneyin. Daha sonra başarılı olup olmadığınıza bakın. Yanıt için 63 almalısınız. [GitHub 'da tamamlanan kodu görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıt görebilirsiniz.

"Dallar ve döngüler" öğreticisini tamamladınız.

Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğreticisiyle devam edebilirsiniz.

Aşağıdaki makalelerde bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:

- [If ve else deyimi](../../language-reference/keywords/if-else.md)
- [While ekstresi](../../language-reference/keywords/while.md)
- [Do deyimi](../../language-reference/keywords/do.md)
- [For deyimleri](../../language-reference/keywords/for.md)
