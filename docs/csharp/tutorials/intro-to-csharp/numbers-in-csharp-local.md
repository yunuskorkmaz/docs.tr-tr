---
title: C# sayılar - C# eğitimine giriş
description: Sayısal türleri, özelliklerini ve yöntemlerini inceleyerek C# öğrenin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7e9af4b3b859f74d7e92ff10b3964ddd59d2473b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156551"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>C'deki integral ve kayan nokta sayılarını işleme\#

Bu öğretici c # interaktif sayısal türleri hakkında öğretir. Küçük miktarlarda kod yazacaksın, sonra bu kodu derleyip çalıştıracaksın. Öğretici C# numaraları ve matematik işlemleri keşfetmek dersler bir dizi içerir. Bu dersler size C# dilinin temel özelliklerini öğretir.

Bu öğretici, geliştirme için kullanabileceğiniz bir makineye sahip olmak için bekliyor. .NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir. Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md) dır.

## <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

*Numbers-quickstart*adlı bir dizin oluşturun. Geçerli dizinini yapın ve aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

En sevdiğiniz düzenleyicide *Program.cs* açın `Console.WriteLine("Hello World!");` ve satırı aşağıdakilerle değiştirin:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.

Az önce tamsayılarla gerçekleştirilen temel matematik işlemlerinden birini gördünüz. Tür, `int` sıfır, pozitif veya negatif tam sayı olan bir **tamsayıyı**temsil eder. Toplama için `+` sembolünü kullanırsınız. Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:

- çıkarma için `-`
- çarpma için `*`
- bölme için `/`

Bu farklı işlemleri keşfederek başlayın. Değerini yazan satırdan sonra bu `c`satırları ekleyin:

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.

Ayrıca dilerseniz aynı satırda birden çok matematik işlemi gerçekleştirerek de deneme yapabilirsiniz. Örneğin `c = a + b - 12 * 17;` deneyin. Değişkenleri ve sabit sayıları karıştırmaya izin verilir.

> [!TIP]
> C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. **Derleyici** bu hataları bulup size bildirir. Çıktı hata iletileri içeriyorsa, neyi düzelteceğimize bakmak için örnek koduna ve pencerenizdeki koda yakından bakın.
> Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.

İlk adımı bitirdin. Bir sonraki bölümü başlatmadan önce, geçerli kodu ayrı bir yönteme taşıyalım. Bu, yeni bir örnekle çalışmaya başlamayı kolaylaştırır. Metodunuzu `WorkingWithIntegers` yeniden adlandırın `Main` `Main` ve `WorkingWithIntegers`çağıran yeni bir yöntem yazın. Bitirdiğinizde, kodunuz şu şekilde görünmelidir:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>İşlem sırasını inceleme

Çağrıyı yorumla. `WorkingWithIntegers()` Bu bölümde çalışırken çıktıdaha az darmadağın yapacaktır:

```csharp
//WorkingWithIntegers();
```

C#'da `//` bir **yorum** başlar. Yorumlar, kaynak kodunuzda tutmak istediğiniz ancak kod olarak yürütülmemek istemediğiniz herhangi bir metindir. Derleyici yorumlardan yürütülebilir bir kod oluşturmaz.

C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.
Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.
Yönteminize `Main` aşağıdaki kodu ekleyerek ve aşağıdakileri `dotnet run`gerçekleştirerek bunu keşfedin:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.

Önce yapılmasını istediğiniz işlem veya işlemlerin etrafına parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz. Aşağıdaki satırları ekleyin ve yeniden çalıştırın:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Birçok farklı işlemi birleştirerek daha fazlasını keşfedin. Yönteminizin `Main` altındaki aşağıdaki satırları gibi bir şey ekleyin. `dotnet run` komutunu yeniden deneyin.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz. Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.

Bu davranışı görmediyseniz, yönteminizin `Main` sonunda aşağıdaki kodu deneyin:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Sonuçları `dotnet run` görmek için yeniden yazın.

Devam etmeden önce, bu bölümde yazdığınız tüm kodları alıp yeni bir yönteme koyalım. Buna yeni `OrderPrecedence`bir yöntem deyin.
Böyle bir şeyle bitirmelisin:

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>Tamsayı duyarlığını ve sınırlarını inceleme

Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir.
Geri **kalanını** **modulo** işleci, `%` karakter kullanarak alabilirsiniz. Yönteminizde `Main` aşağıdaki kodu deneyin:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır. Bu sınırları görmek `Main` için bu kodu yönteminize ekleyin:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir. Yanıtın bir sınırdan diğerine kaydığı görülüyor. Bir örnek görmek `Main` için yönteminize bu iki satırı ekleyin:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin. Bu, `min + 2` ile aynıdır.
Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.
Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.

`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur. Bir sonraki adımda bunları inceleyelim.

Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalım. Bunu, `TestLimits` olarak adlandırın.

## <a name="work-with-the-double-type"></a>Çift tür ile çalışma

`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder. Bu terimler sizin için yeni olabilir. **Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır. **Çift duyarlıklı**, bu sayıların **tek duyarlıktan** daha fazla duyarlık kullanılarak depolandığı anlamına gelir. Modern bilgisayarlarda çift duyarlıklı sayı kullanımı, tek duyarlıklı sayılara göre daha yaygındır.
İnceleyelim mi? Aşağıdaki kodu ekleyin ve sonucu görün:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin. Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür. Şimdiye kadar yazdıkların aşağıdaki kodu deneyin:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Bu değerler bilimsel gösterimde yazdırılır. `E` değerinin sol tarafındaki sayı katsayıdır. Sağ taraftaki sayı 10’un bir kuvveti olarak üstür.

Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir. Şu kodu deneyin:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

`0.3` yinelemesinin `1/3` ile tam olarak aynı olmadığını fark edersiniz.

***Sınama***

`double` türünü kullanarak büyük sayılar, küçük sayılar, çarpma işlemi ve bölme işlemi ile diğer hesaplamaları deneyin. Daha karmaşık hesaplamalar deneyin.

Meydan okumayla biraz zaman geçirdikten sonra, yazdığınız kodu alın ve yeni bir yönteme yerleştirin. Bu yeni `WorkWithDoubles`yöntemi adlandırın.

## <a name="work-with-fixed-point-types"></a>Sabit nokta türleriyle çalışma

C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.  Öğrenmeniz gereken bir tür daha vardır: `decimal` türü. `decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir. **Sabit nokta** terimi, ondalık ayırıcının (veya ikili noktasının) hareket etmediği anlamına gelir. Şimdi buna bir göz atalım:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Aralığın `double` türünden daha küçük olduğuna dikkat edin. Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık olduğunu görebilirsiniz:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz.

Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.

***Sınama***

Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın. Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın. İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.

19 ile 20 arasında bir yanıt almanız gerekir.
[GitHub'daki bitmiş örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.

Dilerseniz diğer formüllerden de deneme yapabilirsiniz.

"C#'daki sayılar" hızlı başlangıcını tamamladınız. Kendi geliştirme ortamınızda [Şubeler ve döngüler](branches-and-loops-local.md) ile hızlı bir şekilde başlatAbilirsiniz.

Aşağıdaki konularda C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:

- [Tamsayı sayısal türler](../../language-reference/builtin-types/integral-numeric-types.md)
- [Kayan nokta sayısal türleri](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md)
