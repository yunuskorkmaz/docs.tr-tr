---
title: Dal ve döngüler Öğreticisi - C# yerel quickstarts
description: Bu hızlı başlangıcı dallar ve döngüler hakkında koşullu dal ve art arda deyimlerini yürütmek için döngüler destekler dili sözdizimi keşfetmek için C# kod yazın.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: a25ea7f266405a017f6f4576659195b2ac1afbf4
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="branches-and-loops"></a>Dal ve döngüler

Bu hızlı başlangıç değişkenlerini inceler ve bu değişkenleri esas alarak yürütme yolu değiştirir kodunun nasıl yazılacağını öğretir. C# kod yazma ve derleme ve onu çalıştırma sonuçları görüntüleyin. Hızlı Başlangıç dallanma ve döngü yapıları C# keşfedin dersleri bir dizi içerir. Bu derslerin C# dil temelleri öğretir.

Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir. Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.

## <a name="make-decisions-using-the-if-statement"></a>Kullanarak kararlar `if` deyimi

Adlı bir dizin oluşturun **dalları Hızlı Başlangıç**. Geçerli dizin çalıştırma yapıp `dotnet new console -n BranchesAndLoops -o .`. Bu komut, geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.Writeline("Hello World!");` aşağıdaki kod ile:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Bu kod yazarak deneyin `dotnet run` içinde, konsol penceresi. "Yanıt 10'dan daha büyük." iletisini görmeniz gerekir konsolunuza yazdırılmıştır.

Bildirimi değiştirme `b` toplam 10'dan az olmasını sağlayın: 

```csharp
int b = 3;
```

Tür `dotnet run` yeniden. Yanıt 10'dan az olduğundan, hiçbir şey yazdırılır. **Koşulu** olduğunuz test değer false. Olası dallarını birini yalnızca yazdıktan çünkü yürütmek için herhangi bir kod olmayan bir `if` deyimi: true dal.

> [!TIP]
> C# (veya herhangi bir programlama dili) keşfetmenizde kodu yazarken hataları hale getireceğiz. Derleyici bulun ve hataları raporlar. Yakından hata çıkış ve hata oluşturulan kod bakın. Derleyici Hatası genellikle sorun bulmanıza yardımcı olabilir.

Bu ilk örnek gücünü gösterir `if` ve Boolean türleri. A *Boolean* iki değerlerden birine sahip bir değişken: `true` veya `false`. C# özel türünü tanımlayan `bool` Boolean değişkenleri için. `if` Deyimi denetler değerini bir `bool`. Değer olduğunda `true`, aşağıdaki deyim `if` yürütür. Aksi takdirde atlanır.

Bu işlem koşullar denetleniyor ve bu koşullara göre deyimleri yürütme çok güçlü bir özelliktir.

## <a name="make-if-and-else-work-together"></a>Olun ve başka birlikte çalışma

Her iki true ve false dallarda farklı kod yürütmek için oluşturduğunuz bir `else` koşul yanlış olduğunda, yürüten dal. Bu deneyin. Aşağıdaki kodda son iki satırı ekleyin, `Main` yöntemi (zaten sahip olmanız gereken ilk dört):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Deyimi aşağıdaki `else` anahtar sözcüğü yürütür yalnızca sınanan koşul olduğunda `false`. Birleştirme `if` ve `else` Boolean ile koşullar sağlar hem işlemek için ihtiyacınız olan tüm güç bir `true` ve `false` koşulu.

> [!IMPORTANT]
> Girinti altında `if` ve `else` deyimleri İnsan okuyucular için değil.
> C# dili girinti veya boşluk önemli olarak kabul etmez. Deyimi aşağıdaki `if` veya `else` anahtar sözcüğü koşula göre yürütülür. Bu hızlı başlangıç tüm örneklerinde satırlarını deyimleri denetim akışı üzerinde göre Girintile yaygın bir uygulama izleyin.

Girinti önemli olmadığı için kullanmanıza gerek `{` ve `}` koşullu yürütür blok parçası olarak birden fazla deyim istediğinizde belirtmek için. C# programcıları genellikle kullanın Bu küme ayraçları tüm `if` ve `else` yan tümceleri. Aşağıdaki örnek, yeni oluşturduğunuz bir ile aynıdır. Aşağıdaki kod eşleştirmek için yukarıdaki kodunuzu değiştirin:

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
> Bu hızlı başlangıç kullanılmadıkları tüm kod örnekleri aşağıdaki küme ayraçları dahil kabul yöntemler.

Daha karmaşık koşullar test edebilirsiniz. Aşağıdaki kodu ekleyin, `Main` yöntemi, o ana kadarki yazılan koddan sonra:

```csharp
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
```

`&&` Temsil eder "ve". Bu koşulların her ikisi de true dalında deyimi yürütmek için doğru olması gerektiği anlamına gelir.  Bunları içine sağlanan bu Ayrıca, her koşullu dal birden fazla deyime olabilir örnekler `{` ve `}`.

Aynı zamanda `||` temsil etmek için "veya". Şu ana kadar yazdıklarınızı sonra aşağıdaki kodu ekleyin:

```csharp
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
```

İlk adım tamamladınız. Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın. Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır. Yeniden Adlandır, `Main` yönteme `ExploreIf` ve yeni bir yazma `Main` çağıran yöntemi `ExploreIf`. İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:

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

Açıklama çağrısı çıkışı `ExploreIf()`. Bu bölümde çalışırken daha az kalabalık çıkış yapar:

```csharp
//ExploreIf();
```

`//` Başlayan bir **açıklama** C#. Kaynak kodunuz tutmak ancak kodu olarak yürütmeme istediğiniz herhangi bir metin açıklamalardır. Derleyici herhangi bir yürütülebilir kod açıklamalardan oluşturmaz.

## <a name="use-loops-to-repeat-operations"></a>Döngüler işlemleri yinelemek için kullanın

Bu bölümde kullandığınız **döngüler** deyimleri yinelenecek. Bu kodda deneyin, `Main` yöntemi:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` İfadesi bir koşulu denetler ve ifadesi veya deyimi blok aşağıdaki yürütür `while`. Art arda koşul ve koşul yanlış olana kadar bu deyimleri yürütme denetler.

Bu örnekte, diğer yeni bir işleç var. `++` Sonra `counter` değişken **artırma** işleci. 1 değerine ekler `counter` ve bu değeri depolar `counter` değişkeni.

> [!IMPORTANT]
> Olduğundan emin olun `while` kod yürütmek gibi Döngü koşulu değişiklikleri false. Aksi takdirde, oluşturduğunuz bir **sonsuz bir döngü** programınızı hiçbir zaman sona ereceği. Değil gösterilmiştir Bu örnekte, kullanarak çıkmak için program zorlamak olduğundan **CTRL-C** veya diğer anlamına gelir.

`while` Döngü kod aşağıdaki yürütmeden önce koşulu sınar `while`. `do` ... `while` döngü kodu ilk yürütür ve koşul denetler. Aşağıdaki kodda döngü gösterilmese yapın:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Bu `do` döngü ve önceki `while` döngü, aynı çıktı üretir.

## <a name="work-with-the-for-loop"></a>Çalışmak döngü için

**İçin** döngü yaygın olarak kullanılan C# '. Bu kod, Main() yönteminin deneyin:

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

Aynı iş olarak bunu yapar `while` döngü ve `do` zaten kullandığınız döngü. `for` Deyimi nasıl çalıştığını denetleyen üç bölümden sahiptir.

İlk bölümüdür **Başlatıcısı için**: `for index = 0;` bildiren `index` döngü değişkendir ve ilk değerini ayarlar `0`.

Orta parçasıdır **koşul için**: `index < 10` bildirir bu `for` sayacın değeri 10'dan az olduğu sürece yürütme döngü devam eder.

Son bölümüdür **yineleyici için**: `index++` blok aşağıdaki yürüttükten sonra Döngü değişkeninin değiştirme belirtir `for` deyimi. Burada, belirtir `index` bloğu yürütür her zaman 1 azaltılır.

Bu kendinizle deneyin. Her birini deneyin:

- Farklı bir değer başlatmak için Başlatıcı değiştirin.
- Farklı bir değer durdurmak için koşulunu değiştirin.

İşiniz bittiğinde, şimdi taşıma açın yazma bazı kendiniz ne öğrendiğinize kullanmak için kodu.

## <a name="combine-branches-and-loops"></a>Dal ve döngüler birleştirin

Gördüğünüz göre `if` deyimi ve C# dil döngü yapıları bkz tüm tamsayılar 1 ila 3 ile tam bölünebilir 20 toplamını bulmak için C# kod yazın.  Aşağıda, birkaç ipucu verilmiştir:

- `%` İşleci, bir bölme işlemi geri kalanı verir.
- `if` Deyimi, bir sayı toplamı parçası olup olmayacağını görmek için koşul verir.
- `for` Döngü, 20'den sayılar 1 için bir dizi adımı yineleyin yardımcı olabilir.

Kendiniz deneyin. Ardından nasıl yaptığınız denetleyin. 63 için bir yanıt almanız gerekir. Tarafından bir olası yanıt görebilirsiniz [tamamlanan kodu Github'da görüntüleme](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

"Dallar ve döngüler" Hızlı Başlangıç tamamladınız.

İle devam edebilirsiniz [dize ilişkilendirme](interpolated-strings-local.md) kendi geliştirme ortamında hızlı başlangıç.

Bu konularda bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:

[Varsa ve else deyimi](../language-reference/keywords/if-else.md)  
[While deyimi](../language-reference/keywords/while.md)  
[Do deyimi](../language-reference/keywords/do.md)  
[For deyimi](../language-reference/keywords/for.md)  
