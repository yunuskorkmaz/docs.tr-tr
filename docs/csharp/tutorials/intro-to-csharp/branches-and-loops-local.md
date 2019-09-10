---
title: Dallar ve döngüler- C# öğreticiye giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli C# olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere kod yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d329a871265ae42918fbf81c42be6667710e4c75
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850813"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dal ve döngü deyimleri ile koşullu mantık öğrenin

Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir. Kod yazar C# ve bunları derleyip çalıştırmaya ilişkin sonuçları görürsünüz. Öğreticide, ' de C#dallanma ve döngü yapılarını keşfeden oluşan bir dizi ders bulunur. Bu dersler, C# dilin temellerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, yerel geliştirme ortamınızı Mac, PC veya Linux üzerinde ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="make-decisions-using-the-if-statement"></a>`if` İfadesini kullanarak kararlar alın

Dallar adlı bir dizin oluşturun **-öğretici**. Geçerli dizini oluşturun ve çalıştırın `dotnet new console -n BranchesAndLoops -o .`. Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide **program.cs** açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Konsol pencerenizi yazarak `dotnet run` bu kodu deneyin. "Yanıt 10 ' dan büyük" iletisini görmeniz gerekir. konsolunuza yazdırılır.

Bildirimi, toplamın 10 `b` ' dan küçük olacak şekilde değiştirin:

```csharp
int b = 3;
```

Yeniden `dotnet run` yazın. Yanıt 10 ' dan az olduğu için hiçbir şey yazdırılmaz. Test ettiğiniz **koşul** false 'tur. Yalnızca bir `if` deyimin olası dallarından birini yazdığınız için yürütülecek bir kodunuz yok: doğru dal.

> [!TIP]
> Keşfederken C# (veya herhangi bir programlama dilini), kod yazarken hata oluşturursunuz. Derleyici hataları bulacak ve rapor eder. Hata çıktısına ve hatayı oluşturan koda yakından bakın. Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.

Bu ilk örnek, `if` ve Boolean türlerin gücünü gösterir. *Boolean* , iki değerden birine sahip olabilir bir değişkendir: `true` veya. `false` C#Boole değişkenleri `bool` için özel bir tür tanımlar. `if` İfade a`bool`değerini denetler. Değer `true`olduğunda, `if` yürütülür ' i izleyen ifade. Aksi takdirde, atlanır.

Bu koşullara göre koşulları denetleme ve deyimleri yürütme işlemi çok güçlüdür.

## <a name="make-if-and-else-work-together"></a>Eğer ve başka bir birlikte çalışır yap

Doğru ve yanlış dallarda farklı kodu yürütmek için, koşul yanlış olduğunda yürütülen bir `else` dal oluşturursunuz. Bunu deneyin. Aşağıdaki kodda bulunan son iki satırı `Main` yöntemine ekleyin (ilk dördü zaten var olmalıdır):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

`else` Anahtar sözcüğünü izleyen ifade yalnızca `false`test edilen koşul olduğunda yürütülür. Ve `if` `true` `false` Boolean koşulları ile birleştirmek, hem hem de bir koşulu işlemek için ihtiyacınız olan tüm gücü sağlar. `else`

> [!IMPORTANT]
> `if` Ve`else` deyimlerinin altındaki girintileme insan okuyucular içindir.
> Dil C# , girintileme veya boşluk olarak kabul etmez.
> `if` Or`else` anahtar sözcüğünü izleyen ifade, koşula göre yürütülür. Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.

Girintileme önemli olmadığından, birden fazla deyimin koşullu olarak yürütülen `{` bloğun `}` bir parçası olmasını istediğiniz zaman göstermek için ve kullanmanız gerekir. C#programcılar genellikle bu ayraçları tüm `if` ve `else` yan tümcelerde kullanır. Aşağıdaki örnek, az önce oluşturduğunuz ile aynıdır. Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:

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

`==` *Eşitlik*için simge testi. ' `==` Yi kullanarak, ' de gördüğünüz şekilde `a = 5`testi, atamanın eşitliğine ayırır.

"Ve" temsil eder. `&&` Doğru dalda deyimin yürütülmesi için her iki koşulun de true olması gerektiği anlamına gelir.  Bu örnekler Ayrıca, ve `{` `}`içinde yer alan her bir koşullu dalda birden çok deyim olduğunu gösterir.

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

`a`, Ve`b`değerlerini değiştirin ve arasında`&&` geçiş yapın.`||` `c` `&&` Ve`||` işleçlerinin nasıl çalıştığını daha fazla anlayacaksınız.

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. Yönteminizi olarak `ExploreIf` yeniden adlandırın ve çağıran `Main` `ExploreIf`yeni bir yöntem yazın. `Main` İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:

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

, `//` İçinde C#bir **yorum** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

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

İfade bir koşulu denetler ve öğesinden sonra deyimin veya bildiri bloğunu `while`yürütür. `while` Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.

Bu örnekte başka bir yeni işleç vardır. Değişken, **artırma** işlecinden `++`sonra. `counter` Değerine `counter` 1 ekler ve bu değeri `counter` değişkende depolar.

> [!IMPORTANT]
> Kodu yürüttüğünüzde `while` döngü koşulunun yanlış olarak değiştiği emin olun. Aksi takdirde, programınızın hiç bitmediğini **sonsuz bir döngü** oluşturursunuz. Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.

`while` Döngü ,`while`sonrasında kodu yürütmeden önce koşulu sınar. `do` ... `while` döngü önce kodu yürütür ve sonra koşulu denetler. Do while döngüsü aşağıdaki kodda gösterilmiştir:

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

**For** döngüsü genellikle ' de C#kullanılır. Main () yönteminde bu kodu deneyin:

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Bu, `while` döngüyle aynı çalışmayı `do` ve zaten kullandığınız döngüyü yapar. `for` İfadesinin nasıl çalıştığını denetleyen üç bölümü vardır.

İlk bölüm **for başlatıcıdır**: `int index = 0;` Loop değişkeni olduğunu bildirir `index` ve başlangıç değerini olarak `0`ayarlar.

Orta kısım **for koşuludur**: `index < 10` sayacın değeri 10 ' dan `for` az olduğu sürece bu döngünün yürütülmeye devam ettiğini bildirir.

Son bölüm, **Yineleyici için**: `index++` `for` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir. Burada, blok her yürütüldüğünde `index` 1 ' in artırılabilmelidir.

Bunlarla deneyin. Aşağıdakilerin her birini deneyin:

- Başlatıcıyı farklı bir değerle başlayacak şekilde değiştirin.
- Koşulu, farklı bir değerde durdurulacak şekilde değiştirin.

İşiniz bittiğinde, öğrendiklerinizi kullanmak için kendinize bir kod yazmak üzere ilerlim.

## <a name="combine-branches-and-loops"></a>Dalları ve döngüleri birleştirme

Artık, ve içindeki `if` C# döngü yapılarını gördüğünüze göre, 3 ' e bölünebilen 1 ile 20 arasındaki C# tüm tamsayıların toplamını bulmak için kod yazıp yazbileceğinizi görün.  İşte birkaç ipucu:

- `%` İşleci, bir bölme işleminin kalanını verir.
- `if` İfade, bir sayının toplamın bir parçası olup olmadığını görmek için koşul sağlar.
- `for` Döngü, 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olabilir.

Kendiniz deneyin. Sonra nasıl yapıldığını kontrol edin. Yanıt için 63 almalısınız. [GitHub 'da tamamlanan kodu görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıt görebilirsiniz.

"Dallar ve döngüler" öğreticisini tamamladınız.

Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğreticisiyle devam edebilirsiniz.

Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [If ve Else deyimleri](../../language-reference/keywords/if-else.md)
- [While ekstresi](../../language-reference/keywords/while.md)
- [Do ekstresi](../../language-reference/keywords/do.md)
- [For deyimleri](../../language-reference/keywords/for.md)
