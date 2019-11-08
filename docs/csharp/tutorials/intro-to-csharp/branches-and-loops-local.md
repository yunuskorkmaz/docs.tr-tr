---
title: Dallar ve döngüler- C# öğreticiye giriş
description: Dallar ve döngüler hakkında bu öğreticide, ifadeleri sürekli C# olarak yürütmek için koşullu dalları ve döngüleri destekleyen dil sözdizimini araştırmak üzere kod yazarsınız.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739131"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dal ve döngü deyimleri ile koşullu mantık öğrenin

Bu öğretici, değişkenleri inceleyen ve bu değişkenlere göre yürütme yolunu değiştiren bir kod yazmayı öğretir. Kod yazar C# ve bunları derleyip çalıştırmaya ilişkin sonuçları görürsünüz. Öğreticide, ' de C#dallanma ve döngü yapılarını keşfeden oluşan bir dizi ders bulunur. Bu dersler, C# dilin temellerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="make-decisions-using-the-if-statement"></a>`if` ifadesini kullanarak kararlar alın

Dallar adlı bir dizin oluşturun *-öğretici*. Geçerli dizini yapın ve şu komutu çalıştırın:

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

En sevdiğiniz düzenleyicide *program.cs* açın ve satır `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Konsol pencerenize `dotnet run` yazarak bu kodu deneyin. "Yanıt 10 ' dan büyük" iletisini görmeniz gerekir. konsolunuza yazdırılır.

Toplamın 10 ' dan küçük olması için `b` ' ın bildirimini değiştirin:

```csharp
int b = 3;
```

`dotnet run` yeniden yazın. Yanıt 10 ' dan az olduğu için hiçbir şey yazdırılmaz. Test ettiğiniz **koşul** false 'tur. Yalnızca bir `if` ifadesine ait olası dallardan birini yazdığınız için yürütülecek bir kodunuz yok: doğru dal.

> [!TIP]
> Keşfederken C# (veya herhangi bir programlama dilini), kod yazarken hata oluşturursunuz. Derleyici hataları bulacak ve rapor eder. Hata çıktısına ve hatayı oluşturan koda yakından bakın. Derleyici hatası genellikle sorunu bulmanıza yardımcı olabilir.

Bu ilk örnekte `if` ve Boole türlerinin gücü gösterilmektedir. *Boole* değeri iki değerden birine sahip olabilir: `true` veya `false`. C#Boole değişkenleri için `bool` özel bir tür tanımlar. `if` bildiri bir `bool`değerini denetler. Değer `true` olduğunda, `if` ' i izleyen ifade yürütülür. Aksi takdirde, atlanır.

Bu koşullara göre koşulları denetleme ve deyimleri yürütme işlemi çok güçlüdür.

## <a name="make-if-and-else-work-together"></a>Eğer ve başka bir birlikte çalışır yap

Doğru ve yanlış dallarda farklı kodu yürütmek için, koşul yanlış olduğunda yürütülen bir `else` dalı oluşturursunuz. Bunu deneyin. Aşağıdaki kodda bulunan son iki satırı `Main` yöntemine ekleyin (ilk dördü zaten var olmalıdır):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

`else` anahtar sözcüğünü izleyen ifade, yalnızca test edilen koşul `false`olduğunda yürütülür. `if` ve `else` Boole koşullarına göre birleştirmek, hem `true` hem de `false` koşulunu işlemek için ihtiyacınız olan tüm gücü sağlar.

> [!IMPORTANT]
> `if` ve `else` deyimlerinin altındaki girintileme insan okuyucular içindir.
> Dil C# , girintileme veya boşluk olarak kabul etmez.
> `if` veya `else` anahtar sözcüğünü izleyen ifade, koşula bağlı olarak yürütülür. Bu öğreticideki tüm örnekler, ifadelerin denetim akışına göre satırları girintilemek için ortak bir uygulama izler.

Girintileme önemli olmadığından, çok sayıda deyimin koşullu olarak yürütülen bloğun bir parçası olmasını istediğiniz zaman göstermek için `{` ve `}` ' i kullanmanız gerekir. C#programcılar genellikle bu ayraçları tüm `if` ve `else` yan tümcelerinde kullanır. Aşağıdaki örnek, az önce oluşturduğunuz ile aynıdır. Yukarıdaki kodu aşağıdaki kodla eşleşecek şekilde değiştirin:

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

Daha karmaşık koşulları test edebilirsiniz. Şu ana kadar yazdığınız koddan sonra `Main` yöntetiniz için aşağıdaki kodu ekleyin:

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

*Eşitlik*için `==` sembol testi. `==` kullanmak, `a = 5`' de gördüğünüz sınav için testi birbirinden ayırır.

`&&` "ve" temsil eder. Doğru dalda deyimin yürütülmesi için her iki koşulun de true olması gerektiği anlamına gelir.  Bu örnekler Ayrıca, `{` ve `}` ' de yer alan her bir koşullu dalda birden çok deyim olduğunu gösterir.

Ayrıca, "veya" öğesini göstermek için `||` de kullanabilirsiniz. Şu ana kadar yazıldıktan sonra aşağıdaki kodu ekleyin:

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

`a`, `b`ve `c` değerlerini değiştirip `&&` ile `||` arasında geçiş yapın. `&&` ve `||` işleçlerinin nasıl çalıştığını daha iyi anlayabilirsiniz.

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. `Main` yönteminizi `ExploreIf` olarak yeniden adlandırın ve `ExploreIf`çağıran yeni bir `Main` yöntemi yazın. İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:

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

`ExploreIf()`çağrısını açıklama. Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//ExploreIf();
```

`//` içinde C#bir **yorum** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

## <a name="use-loops-to-repeat-operations"></a>İşlemleri yinelemek için döngüleri kullanma

Bu bölümde deyimlerini yinelemek için **döngüleri** kullanırsınız. `Main` yönteminde bu kodu deneyin:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` bildiri bir koşulu denetler ve `while`takip eden deyimin veya bildiri bloğunu yürütür. Koşul false olana kadar durumu sürekli olarak denetler ve bu deyimleri gerçekleştirir.

Bu örnekte başka bir yeni işleç vardır. `counter` değişkenden sonra `++` **artırma** işleçtir. `counter` değerine 1 ekler ve bu değeri `counter` değişkeninde depolar.

> [!IMPORTANT]
> Kodu yürütmeden `while` Loop koşulunun false olarak değiştiği emin olun. Aksi takdirde, programınızın hiç bitmediğini **sonsuz bir döngü** oluşturursunuz. Bu örnekte gösterilmediği için, programınızı **CTRL-C** veya başka yollarla çıkmaya zorlamaya zorlamanız gerekir.

`while` döngüsü, `while`takip eden kodu yürütmeden önce koşulu sınar. `do`... `while` döngüsü önce kodu yürütür ve sonra koşulu kontrol eder. Do while döngüsü aşağıdaki kodda gösterilmiştir:

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Bu `do` döngüsü ve önceki `while` döngüsü aynı çıktıyı üretir.

## <a name="work-with-the-for-loop"></a>For döngüsü ile çalışma

**For** döngüsü genellikle ' de C#kullanılır. Main () yönteminde bu kodu deneyin:

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Bu, `while` döngüsü ile aynı çalışmayı ve zaten kullandığınız `do` döngüsünü yapar. `for` deyimin nasıl çalıştığını denetleyen üç bölümü vardır.

İlk bölüm **for başlatıcıdır**: `int index = 0;` `index` döngü değişkeni olduğunu bildirir ve başlangıç değerini `0`olarak ayarlar.

Orta kısım **için olan durumdur**: `index < 10` sayaç değeri 10 ' dan az olduğu sürece bu `for` döngüsünün yürütülmeye devam ettiğini bildirir.

Son bölüm **Yineleyici için**: `index++` `for` deyimden sonra blok yürütüldükten sonra döngü değişkeninin nasıl değiştirileceğini belirtir. Burada, blok her çalıştırıldığında `index` 1 ' in artırılabilmelidir.

Bunlarla deneyin. Aşağıdakilerin her birini deneyin:

- Başlatıcıyı farklı bir değerle başlayacak şekilde değiştirin.
- Koşulu, farklı bir değerde durdurulacak şekilde değiştirin.

İşiniz bittiğinde, öğrendiklerinizi kullanmak için kendinize bir kod yazmak üzere ilerlim.

## <a name="combine-branches-and-loops"></a>Dalları ve döngüleri birleştirme

Artık `if` ifadesini ve bu C# dilin döngü yapılarını gördüğünüze göre, 3 ' e bölünebilen 1 ile 20 C# arasındaki tüm tamsayıların toplamını bulmak için kod yazıp yazbileceğinizi inceleyin.  İşte birkaç ipucu:

- `%` işleci, bir bölme işleminin kalanını sağlar.
- `if` ifade, bir sayının toplamın bir parçası olup olmadığını görmek için koşul sağlar.
- `for` döngüsü, 1 ile 20 arasındaki tüm sayılar için bir dizi adımı yinelemenize yardımcı olabilir.

Kendiniz deneyin. Sonra nasıl yapıldığını kontrol edin. Yanıt için 63 almalısınız. [GitHub 'da tamamlanan kodu görüntüleyerek](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54)olası bir yanıt görebilirsiniz.

"Dallar ve döngüler" öğreticisini tamamladınız.

Kendi geliştirme ortamınızda [diziler ve koleksiyonlar](arrays-and-collections.md) öğreticisiyle devam edebilirsiniz.

Bu kavramlar hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [If ve Else deyimleri](../../language-reference/keywords/if-else.md)
- [While ekstresi](../../language-reference/keywords/while.md)
- [Do ekstresi](../../language-reference/keywords/do.md)
- [For deyimleri](../../language-reference/keywords/for.md)
