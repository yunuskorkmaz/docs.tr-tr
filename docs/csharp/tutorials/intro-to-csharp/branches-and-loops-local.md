---
title: Dallar ve döngüler - Giriş C# Öğreticisi
description: Dallar ve döngüler hakkındaki Bu öğreticide, yazdığınız C# koşullu dallar ve döngüler deyimleri tekrar tekrar yürütmenin destekleyen dili sözdizimi keşfetmek için kod.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 4a116ae5294915770dec742c147cf2ba1bf6e284
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427259"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a>Dal ve döngü deyimleriyle koşullu mantık öğrenin

Bu öğretici size değişkenleri araştıran ve yürütme yolunu Bu değişkenlere göre değiştiren bir kodun nasıl yazılacağını öğretir. C# kodu yazacak ve derleyerek ve çalıştırarak bunu sonuçlarını göreceksiniz. Öğreticiyi içeren bir dizi, dallanma ve döngü yapıları içindeki keşfedin Ders C#. Bu dersler size C# dilinin temellerini öğretin.

Bu öğretici geliştirme için kullanabileceğiniz bir makine olmasını bekliyor. .NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte.

## <a name="make-decisions-using-the-if-statement"></a>Kullanarak kararlar `if` deyimi

Adlı bir dizin oluşturmak **dalları-tutorial**. Geçerli dizin ve çalışma olun `dotnet new console -n BranchesAndLoops -o .`. Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.

Açık **Program.cs** satırı değiştirin ve tercih ettiğiniz düzenleyiciyi `Console.WriteLine("Hello World!");` aşağıdaki kod ile:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Bu kod yazarak deneme `dotnet run` konsol pencerenizde. "Yanıt 10'dan büyük sağlıyor." iletisini görmeniz gerekir konsolunuza yazdırılmasını.

Değiştirin `b` böylece toplam 10'dan küçük:

```csharp
int b = 3;
```

Tür `dotnet run` yeniden. Yanıt 10'dan küçük olduğundan herhangi bir şey yazdırılmaz. **Koşul** olduğunuz test değer false. İçin olası dallardan birine yalnızca yazdığınız yürütülecek herhangi bir kodu olmayan bir `if` deyimi: true dalı.

> [!TIP]
> C# (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. Derleyici, bulun ve hataları bildirin. Hata çıkış ve hatayı oluşturan kodu yakından bakın. Derleyici Hatası genellikle sorun bulmanıza yardımcı olabilir.

İlk örnek gücünü gösterir `if` ve Boole türlerini. A *Boole* iki değerden birine sahip olabilen bir değişkendir: `true` veya `false`. C#özel bir tür tanımlar `bool` Boole değişkenleri için. `if` Deyimi değerini denetler bir `bool`. Değer olduğunda `true`, sonrasındaki deyime `if` yürütür. Aksi halde atlanır.

Koşulları kontrol etmek ve bu koşullara göre deyimleri yürütmek için gerçekleştirilen bu işlem son derece etkilidir.

## <a name="make-if-and-else-work-together"></a>İf ve else koşullarını birlikte

Hem true hem de false dallarında farklı kod yürütmek için oluşturduğunuz bir `else` dalı, koşul false olduğunda yürütür. Bu deneyin. Aşağıdaki kodda için son iki satırı ekleyin, `Main` yöntemi (zaten ilk dört):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Deyim `else` anahtar sözcüğü, yalnızca test edilen koşul olduğunda yürütür `false`. Birleştirme `if` ve `else` Boole koşullarıyla koşullar sağlar hem de işlemek için ihtiyacınız olan tüm etkiyi bir `true` ve `false` koşul.

> [!IMPORTANT]
> Altındaki girinti `if` ve `else` deyimleri, İnsan okuyuculara yöneliktir.
> C# dili girintileri veya boşlukları olarak önemli kabul etmez.
> Deyim `if` veya `else` anahtar sözcüğü, bir koşula göre yürütülecek. Bu öğreticideki tüm örnekler üzerinde deyimlerin denetim akışına bağlı olarak satır girintilemenin sık kullanılan bir yöntemini uygulayın.

Girinti önemli olmadığı için kullanmanız gerekir `{` ve `}` koşullu olarak yürütülen bloğun parçası olarak birden fazla deyim istediğinizde belirtmek için. C# programcıları genellikle kullanır Bu ayraçları tüm `if` ve `else` yan tümceleri. Aşağıdaki örnek, oluşturduğunuz bir ile aynıdır. Aşağıdaki kod eşleştirmek için yukarıdaki kodunuzu değiştirin:

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
> Bu öğreticinin geri kalanını, sonraki küme ayraçlarını, tüm kod örnekleri dahil kabul edilen yöntemleri.

Daha karmaşık koşulları test edebilirsiniz. Aşağıdaki kodu ekleyin, `Main` yöntemi, şimdiye yazılan koddan sonra:

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

`==` İçin testler sembolü *eşitlik*. Kullanarak `==` eşitliği testi gördüğünüz atamanın'öğesinden ayırır `a = 5`.

`&&` Temsil eder "ve". Bu koşulların her ikisi de deyimi true dalında yürütmek için true anlamına gelir.  İçine alınmaları koşuluyla her koşullu dalda birden çok deyime sahip bu örnek ayrıca Göster `{` ve `}`.

Ayrıca `||` temsil etmek için "veya". Şu ana kadar yazdıklarınızı sonra aşağıdaki kodu ekleyin:

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

Değerleri Değiştir `a`, `b`, ve `c` arasında geçiş `&&` ve `||` keşfetmek için. Daha fazla bilgiye nasıl elde etmenizi sağlayacak `&&` ve `||` işleçleri çalışır.

İlk adımı tamamladınız. Sonraki bölümde başlamadan önce geçerli kodu ayrı bir yöntem geçelim. Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır. Yeniden adlandırma, `Main` yönteme `ExploreIf` ve yeni bir yazma `Main` metoduna çağrı yapan `ExploreIf`. İşiniz bittiğinde, kodunuzun şu şekilde görünmelidir:

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

Çağrı yorum `ExploreIf()`. Bu, bu bölümde çalışırken daha az dağınıktır çıkış yapar:

```csharp
//ExploreIf();
```

`//` Başlatan bir **yorum** içinde C#. Kaynak kodunuzu korumakla birlikte kod olarak yürütmeme istediğiniz herhangi bir metin açıklamaları bulunmaktadır. Derleyicinin açıklamaları herhangi bir yürütülebilir kod oluşturmaz.

## <a name="use-loops-to-repeat-operations"></a>İşlemleri yinelemek için döngüleri kullanma

Bu bölümde kullandığınız **döngüler** deyimleri yinelemek için. Bu kodu deneyin, `Main` yöntemi:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while` Deyimi bir koşulu kontrol eder ve deyimi veya deyim bloğunu izleyen yürütür `while`. Art arda koşulu ve koşul false olana kadar bu deyimleri yürütmeyi denetler.

Bu örnekte diğer bir yeni işleç yoktur. `++` Sonra `counter` değişkendir **artışı** işleci. Değerine 1 ekler `counter` ve değeri depolar `counter` değişkeni.

> [!IMPORTANT]
> Emin olun `while` siz kodu yürütürken gibi Döngü koşulu değişiklikleri false. Aksi halde, oluşturduğunuz bir **sonsuz döngü** programınızı hiçbir zaman sona ereceği. Bu değil gösterilmiştir Bu örnekte, programınızı kullanarak çıkmak için zorlamak sahip olduğunuz için **CTRL-C** veya diğer anlamına gelir.

`while` Döngü, sonraki kodu yürütmeden önce koşulu test eder `while`. `do` ... `while` döngüsü önce kodu yürütür ve sonra koşulu kontrol eder. Döngü, aşağıdaki kodda gösterilen sırada yapın:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Bu `do` döngüsü ve önceki `while` döngü, aynı çıktı üretir.

## <a name="work-with-the-for-loop"></a>Çalışmak for döngüsü

**İçin** döngü kullanılan yaygın olarak C#. Bu kodu Main() yönteminizde deneyin:

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

Bu aynı işlevi görür `while` döngü ve `do` zaten kullandığınız döngü. `for` Deyimi nasıl çalıştığını denetleyen üç bölümü vardır.

İlk bölüm **for başlatıcısıdır**: `int index = 0;` bildiren `index` Döngü değişkeninin ve bunun başlangıçtaki değerini ayarlar `0`.

Ortadaki bölüm **koşulu**: `index < 10` bildirir bu `for` döngü sayacının değerini 10'dan az olduğu sürece yürütülmeye devam eder.

Son bölüm ise **yineleyici için**: `index++` nasıl blok yürütüldükten sonra Döngü değişkeninin değiştirileceğini belirtir `for` deyimi. Burada, belirtir `index` bloğun her zaman 1 tarafından arttırılarak.

Bunları kendiniz deneyin. Her birini deneyin:

- Farklı bir değerde başlamak için başlatıcıyı değiştirin.
- Farklı bir değerde durmak için koşulu değiştirin.

İşiniz bittiğinde yazma adımına geçelim bazı öğrendikleriniz kullanılacak kodunu kendiniz.

## <a name="combine-branches-and-loops"></a>Dalları ve döngüleri birleştirme

Gördüğünüze göre `if` deyimini ve döngü yapılarını C# dil bkz 1 ile 3 ile bölünebilen 20 tüm tamsayıların toplamını bulmak için C# kodu yazacak.  Bazı ipuçları şunlardır:

- `%` İşleci size bölme işlemindeki kalanı verir.
- `if` Deyimi bir sayı toplamı parçası olup olmayacağını görmek için koşul sağlar.
- `for` Yinelemenize yardımcı olur, 20'den sayılar 1 için bir dizi adımı yineleyin.

Kendiniz deneyin. Ardından olup olmadığınıza bakın. 63 için bir yanıt almanız gerekir. Olası bir yanıt olarak gördüğünüz [tamamlanan kodu Github'da görüntüleme](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).

"Dallar ve döngüler" öğreticisini tamamladınız.

İle devam edebilir [diziler ve Koleksiyonlar](arrays-and-collections.md) kendi geliştirme ortamınızda öğretici.

Aşağıdaki konulardan Bu kavramlar hakkında daha fazla bilgi edinebilirsiniz:

- [Varsa ve else deyimi](../../language-reference/keywords/if-else.md)
- [While deyimi](../../language-reference/keywords/while.md)
- [Do deyimi](../../language-reference/keywords/do.md)
- [For deyimi](../../language-reference/keywords/for.md)
