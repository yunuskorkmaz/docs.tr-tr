---
title: C# C#
description: Sayısal C# türleri, özelliklerini ve yöntemlerini inceleyerek bilgi edinin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7537bb597665461021946a792e342149f29c0e95
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694666"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>C\# integral ve kayan nokta numaralarını işleme

Bu öğretici, size etkileşimli olarak C# sayısal türler öğretir. Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız. Öğreticide, içindeki C#sayıları ve matematik işlemlerini keşfettiği bir dizi ders bulunur. Bu dersler size C# dilinin temel özelliklerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

Sayı adlı bir dizin oluşturun *-hızlı başlangıç*. Geçerli dizini yapın ve şu komutu çalıştırın:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

En sevdiğiniz düzenleyicide *program.cs* açın ve satır `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Komut pencerenize `dotnet run` yazarak bu kodu çalıştırın.

Az önce tamsayılarla gerçekleştirilen temel matematik işlemlerinden birini gördünüz. `int` türü bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder. Toplama için `+` sembolünü kullanırsınız. Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:

- çıkarma için `-`
- çarpma için `*`
- bölme için `/`

Bu farklı işlemleri keşfederek başlayın. `c`değerini yazan satırdan sonra bu satırları ekleyin:

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

Ayrıca dilerseniz aynı satırda birden çok matematik işlemi gerçekleştirerek de deneme yapabilirsiniz. Örneğin `c = a + b - 12 * 17;` deneyin. Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.

> [!TIP]
> C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. **Derleyici** bu hataları bulup size bildirir. Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.
> Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. `Main` yönteminizi `WorkingWithIntegers` olarak yeniden adlandırın ve `WorkingWithIntegers`çağıran yeni bir `Main` yöntemi yazın. Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:

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

`WorkingWithIntegers()`çağrısını açıklama. Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//WorkingWithIntegers();
```

`//` içinde C#bir **yorum** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar.
Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir.
`Main` yöntemine aşağıdaki kodu ekleyerek ve `dotnet run`yürüterek bunu keşfedebilirsiniz:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.

Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz. Aşağıdaki satırları ekleyin ve yeniden çalıştırın:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Birçok farklı işlemi birleştirerek daha fazlasını keşfedin. `Main` yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin. `dotnet run` komutunu yeniden deneyin.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz. Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.

Bu davranışı görmediyseniz, `Main` yönteminizin sonunda aşağıdaki kodu deneyin:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Sonuçları görmek için yeniden `dotnet run` yazın.

' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz. Yeni yöntemin `OrderPrecedence`çağırın.
Şöyle bir işlem yapmanız gerekir:

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
`%` karakteri olan **Modül** işlecini kullanarak **kalanı** alabilirsiniz. `Main` yönteminde aşağıdaki kodu deneyin:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır. Bu sınırları görmek için bu kodu `Main` yöntemine ekleyin:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir. Yanıtın bir sınırdan diğerine kaydığı görülüyor. Örnek görmek için bu iki satırı `Main` yöntemine ekleyin:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin. Bu, `min + 2` ile aynıdır.
Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**.
Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.

`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur. Bir sonraki adımda bunları inceleyelim.

Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim. Bunu, `TestLimits` olarak adlandırın.

## <a name="work-with-the-double-type"></a>Çift tür ile çalışma

`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder. Bu terimler sizin için yeni olabilir. **Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır. **Çift duyarlıklı**, bu sayıların **tek duyarlıktan** daha fazla duyarlık kullanılarak depolandığı anlamına gelir. Modern bilgisayarlarda çift duyarlıklı sayı kullanımı, tek duyarlıklı sayılara göre daha yaygındır.
İnceleyelim mi? Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:

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

Çift değerin aralığı, tamsayı değerlerinden çok daha büyüktür. Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:

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

***Görev***

`double` türünü kullanarak büyük sayılar, küçük sayılar, çarpma işlemi ve bölme işlemi ile diğer hesaplamaları deneyin. Daha karmaşık hesaplamalar deneyin.

Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin. Yeni yöntemin `WorkWithDoubles`adı.

## <a name="work-with-fixed-point-types"></a>Sabit nokta türleriyle çalışma

C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.  Öğrenmeniz gereken bir tür daha vardır: `decimal` türü. `decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir. **Sabit nokta** terimi, ondalık ayırıcının (veya ikili noktasının) hareket etmediği anlamına gelir. Bir göz atalım:

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

***Görev***

Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın. Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın. İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir.

19 ile 20 arasında bir yanıt almanız gerekir.
[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.

Dilerseniz diğer formüllerden de deneme yapabilirsiniz.

"Numaraları C#" hızlı başlangıç adımlarını tamamladınız. Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.

Aşağıdaki konularda C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:

- [Integral sayısal türleri](../../language-reference/builtin-types/integral-numeric-types.md)
- [Kayan nokta sayısal türleri](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md)
