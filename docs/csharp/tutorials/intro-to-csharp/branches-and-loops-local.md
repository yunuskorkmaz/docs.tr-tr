---
title: Dallar ve döngüler-C# öğreticisine giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere C# kodu yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d8c10a7462b7c27c5353aee6d957732a8d161015
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135951"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dal ve döngü deyimleri ile koşullu mantık öğrenin

Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir. C# kodu yazar ve bunu derleyip çalıştırmanın sonuçlarını görürsünüz. Öğretici, C# ' de dallanma ve döngü yapılarını keşfetmenizi sağlayan bir dizi ders içerir. Bu dersler size C# dilinin temel özelliklerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="make-decisions-using-the-if-statement"></a>`if` İfadesini kullanarak kararlar alın

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

Konsol pencerenizi yazarak `dotnet run` bu kodu deneyin. "Yanıt 10 ' dan büyük" iletisini görmeniz gerekir. konsolunuza yazdırılır.

`b` tanımlamasını toplamın 10’dan küçük olacağı şekilde değiştirin:

```csharp
int b = 3;
```

Yeniden `dotnet run` yazın. Yanıt 10’dan küçük olduğundan herhangi bir şey yazdırılmaz. Test ettiğiniz **koşul** false değerindedir. Bir `if` deyimi için olası dallardan yalnızca birini (true dalı) yazdığınızdan, yürütülecek herhangi bir kodunuz yoktur.

> [!TIP]
> C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. Derleyici hataları bulacak ve rapor eder. Hata çıktısına ve hatayı oluşturan koda yakından bakın. Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.

Bu ilk örnek, `if` ve Boolean türlerin gücünü gösterir. *Boolean* , iki değerden birine sahip olabilir bir değişkendir: `true` veya. `false` C#, `bool` Boole değişkenleri için özel bir tür tanımlar. `if` deyimi bir `bool` için değeri kontrol eder. Değer `true` olduğunda, `if` deyiminden sonra gelen deyim yürütülür. Aksi halde atlanır.

Koşulları kontrol etmek ve bu koşullara göre deyimleri yürütmek için gerçekleştirilen bu işlem son derece etkilidir.

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

`else` anahtar sözcüğünden sonraki deyim, yalnızca test edilen koşul `false` olduğunda yürütülür. Ve `if` `else` Boolean koşulları ile birleştirmek, hem hem de `true` bir `false` koşulu işlemek için ihtiyacınız olan tüm gücü sağlar.

> [!IMPORTANT]
> `if` ve `else` deyimlerinin altındaki girinti, insan okuyuculara yöneliktir.
> C# dili, girintileme veya boşluk olarak kabul etmez.
> `if` veya `else` anahtar sözcüğünden sonra gelen deyim, koşula bağlı olarak yürütülür. Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.

Girinti dikkate alınmadığından, koşullu olarak yürütülen bloğun birden çok deyim içermesini istediğinizde bunu belirtmek için `{` ve `}` ayraçlarını kullanmanız gerekir. C# programcıları bu ayraçları genellikle tüm `if` and `else` tümcelerinde kullanır. Aşağıdaki örnek, az önce oluşturduğunuz ile aynıdır. Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:

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

Daha karmaşık koşulları test edebilirsiniz. Şu ana kadar yazdığınız koddan sonra `Main` aşağıdaki kodu yöntemine ekleyin:

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

Eşitlik `==` için simge testi *equality*. ' `==` Yi kullanarak, ' de gördüğünüz şekilde `a = 5`testi, atamanın eşitliğine ayırır.

`&&` "ve" sözcüğünü ifade eder. Bu, deyimi true dalında yürütmek için her iki koşulun da true olması gerektiği anlamına gelir.  Bu örnekler aynı zamanda, `{` ve `}` ayraçları içine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip olabileceğinizi de gösterir.

"Veya" öğesini `||` göstermek için de kullanabilirsiniz. Şu ana kadar yazıldıktan sonra aşağıdaki kodu ekleyin:

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

`a`, `b`Ve `c` değerlerini değiştirin ve arasında `&&` `||` geçiş yapın. `&&` Ve `||` işleçlerinin nasıl çalıştığını daha fazla anlayacaksınız.

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. `Main` Yönteminizi `ExploreIf` olarak yeniden adlandırın ve çağıran `Main` `ExploreIf`yeni bir yöntem yazın. İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:

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

Çağrısını not edin `ExploreIf()`. Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//ExploreIf();
```

C# `//` dilinde bir **Açıklama** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

## <a name="use-loops-to-repeat-operations"></a>İşlemleri yinelemek için döngüleri kullanma

Bu bölümde deyimlerini yinelemek için **döngüleri** kullanırsınız. Bu kodu `Main` yönteminizin içinde deneyin:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` İfade bir koşulu denetler ve öğesinden sonra deyimin veya bildiri bloğunu yürütür `while`. Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.

Bu örnekte diğer bir yeni işleç mevcuttur. `counter` değişkeninden sonra gelen `++`, **artırma** işlecidir. Değerine 1 ekler `counter` ve bu değeri `counter` değişkende depolar.

> [!IMPORTANT]
> Kodu yürüttüğünüzde `while` döngü koşulunun yanlış olarak değiştiği emin olun. Aksi halde, programınızın hiç sona ermediği **sonsuz bir döngü** oluşturmuş olursunuz. Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.

`while` döngüsü, `while` koşulundan sonraki kodu yürütmeden önce koşulu test eder. `do` ... `while` döngüsü önce kodu yürütür, sonra koşulu kontrol eder. Do while döngüsü aşağıdaki kodda gösterilmiştir:

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

Bu, `while` döngüsü ve zaten kullandığınız `do` döngüsü ile aynı işlevi görür. `for` deyiminde, bunu nasıl çalıştığını denetleyen üç bölüm bulunur.

İlk bölüm **for başlatıcıdır**: `int index = 0;` Loop değişkeni olduğunu bildirir `index` ve başlangıç değerini olarak `0`ayarlar.

Orta kısım **for koşuludur**: `index < 10` sayacın değeri 10 ' dan `for` az olduğu sürece bu döngünün yürütülmeye devam ettiğini bildirir.

Son bölüm, **Yineleyici için**: `index++` `for` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir. Bu bölüm, bloğun her yürütme işleminde `index` değişkeninin 1 artırılması gerektiğini belirtir.

Bunları kendiniz deneyin. Aşağıdakilerden her birini deneyin:

- Farklı bir değerde başlamak için başlatıcıyı değiştirin.
- Farklı bir değerde durmak için koşulu değiştirin.

İşiniz bittiğinde öğrendiklerinizi kullanmak için kendi kendinize kod yazma adımına geçelim.

## <a name="created-nested-loops"></a>İç içe geçmiş döngüler oluşturuldu

Ya `while` `for` da `do` döngüsü, iç döngüde her öğe ile dış döngüdeki her bir öğenin birleşimini kullanarak bir matris oluşturmak için başka bir döngünün içinde iç içe olabilir. Satırları ve sütunları temsil etmek için alfasayısal çiftler kümesi oluşturmayı görelim.

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

Aşağıdaki konulardan bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:

- [If ve else deyimi](../../language-reference/keywords/if-else.md)
- [While ekstresi](../../language-reference/keywords/while.md)
- [Do deyimi](../../language-reference/keywords/do.md)
- [For deyimleri](../../language-reference/keywords/for.md)
