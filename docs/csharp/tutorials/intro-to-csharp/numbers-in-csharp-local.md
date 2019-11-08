---
title: C# C#
description: Sayısal C# türleri, özelliklerini ve yöntemlerini inceleyerek bilgi edinin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: a06bc57e5c979b62e19407747cb2c8a2447ca114
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739143"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>C \# integral ve kayan nokta numaralarını işleme

Bu öğretici, size etkileşimli olarak C# sayısal türler öğretir. Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız. Öğreticide, içindeki C#sayıları ve matematik işlemlerini keşfettiği bir dizi ders bulunur. Bu dersler, C# dilin temellerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="explore-integer-math"></a>Tamsayı matematiğini keşfet

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

Yalnızca tamsayılarla temel matematik işlemlerinden birini gördünüz. `int` türü bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder. Ek için `+` sembolünü kullanırsınız. Tamsayılar için diğer yaygın matematik işlemleri şunlardır:

- çıkarma için `-`
- Çarpma için `*`
- Bölüm için `/`

Bu farklı işlemleri inceleyerek başlayın. `c`değerini yazan satırdan sonra bu satırları ekleyin:

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

İsterseniz aynı satırda birden çok matematik işlemi gerçekleştirerek da deneyebilirsiniz. Örneğin `c = a + b - 12 * 17;` deneyin. Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.

> [!TIP]
> Keşfederken C# (veya herhangi bir programlama dilini), kod yazarken hata oluşturursunuz. **Derleyici** bu hataları bulacak ve size rapor eder. Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.
> Bu alıştırma, C# kod yapısını öğrenmenize yardımcı olur.

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

## <a name="explore-order-of-operations"></a>İşlem sırasını keşfet

`WorkingWithIntegers()`çağrısını açıklama. Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//WorkingWithIntegers();
```

`//` içinde C#bir **yorum** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

C# Dil, matematiksel olarak öğrendiğiniz kurallarla tutarlı kurallara sahip farklı matematik işlemlerinin önceliğini tanımlar.
Çarpma ve bölme, toplama ve çıkarma konusunda önceliklidir.
`Main` yöntemine aşağıdaki kodu ekleyerek ve `dotnet run`yürüterek bunu keşfedebilirsiniz:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Çıktı, çarpma 'nın ekleme işleminden önce gerçekleştirildiğini gösterir.

Önce gerçekleştirilmesini istediğiniz işlemin veya işlemlerin çevresine parantez ekleyerek farklı bir işlem sırası zorlayabilirsiniz. Aşağıdaki satırları ekleyin ve yeniden çalıştırın:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Birçok farklı işlemi birleştirerek daha fazlasını keşfedebilirsiniz. `Main` yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin. Yeniden `dotnet run` deneyin.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Tamsayılar için ilginç bir davranış fark etmiş olabilirsiniz. Sonucun ondalık veya kesir kısmını içermesini bekleseniz bile, tam sayı bölümü her zaman bir tamsayı sonucu üretir.

Bu davranışı görmediyseniz, `Main` yönteminizin sonunda aşağıdaki kodu deneyin:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Sonuçları görmek için yeniden `dotnet run` yazın.

' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz. Yeni yöntemin `OrderPrecedence` çağırın.
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

## <a name="explore-integer-precision-and-limits"></a>Tamsayı hassasiyetini ve limitleri keşfet

Bu son örnek, bu tamsayı bölümünün sonucu ne olduğunu gösterdi.
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

C# Tamsayı türü matematik tamlarından farklı bir şekilde farklılık gösterir: `int` türü en az ve en fazla sınırlara sahiptir. Bu sınırları görmek için bu kodu `Main` yöntemine ekleyin:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Hesaplama bu sınırları aşan bir değer üretirse, bir **yetersiz** yer veya **taşma** koşulunuz vardır. Yanıt bir sınırdan diğerine kaydırılır. Örnek görmek için bu iki satırı `Main` yöntemine ekleyin:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Yanıtın en düşük (negatif) tamsayıya çok yakın olduğuna dikkat edin. `min + 2`aynıdır.
Toplama işlemi, tamsayılar için izin verilen değerleri **taşırdı** .
Bir taşma, olası en büyük tamsayı değerinden en küçüğe "kaydırdığı için, yanıt çok büyük negatif bir sayıdır.

`int` türü gereksinimlerinizi karşılamıyorsa kullanabileceğiniz farklı sınırlara ve duyarlığa sahip başka sayısal türler vardır. Bundan sonra bu ileri keşfedelim.

Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim. `TestLimits`adlandırın.

## <a name="work-with-the-double-type"></a>Double türüyle çalışma

`double` sayısal türü bir çift duyarlıklı kayan noktalı sayıyı temsil eder. Bu terimler sizin için yeni olabilir. **Kayan noktalı** sayı, çok büyük veya küçük olabilecek tamsayı olmayan sayıları temsil etmek için kullanışlıdır. **Çift duyarlıklı** , bu sayıların **tek duyarlığa**göre daha fazla duyarlık kullanılarak depolandığı anlamına gelir. Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır.
Keşfedelim. Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin. Double değerleri ile biraz daha karmaşık bir ifade deneyin:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

Double değerinin aralığı tamsayı değerlerinden çok daha büyüktür. Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Bu değerler bilimsel gösterimde yazdırılır. `E` solundaki sayı mantisinin ' dir. Sağdaki sayı, 10 ' un üssü olarak üs değeri olan sayıdır.

Matematiği gibi ondalık sayılar gibi, içindeki Double C# değerleri de yuvarlama hataları içerebilir. Şu kodu deneyin:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Yinelenen `0.3` `1/3` tam olarak aynı olmadığını bilirsiniz.

***Sına***

`double` türünü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin. Daha karmaşık hesaplamalar deneyin.

Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin. Yeni yöntemin `WorkWithDoubles` adı.

## <a name="work-with-fixed-point-types"></a>Sabit nokta türleriyle çalışma

Temel sayısal türleri C#: tamsayılar ve Double değerleri ile gördünüz.  Öğreneceğinizi bir başka tür vardır: `decimal` türü. `decimal` türü daha küçük bir aralığa sahiptir, ancak `double`daha fazla duyarlığa sahiptir. **Sabit nokta** terimi, ondalık noktanın (veya ikili noktanın) taşınmayacağı anlamına gelir. Şimdi bir göz atalım:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Aralığın `double` türünden küçük olduğuna dikkat edin. Aşağıdaki kodu deneyerek ondalık türüyle daha büyük duyarlık görebilirsiniz:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Sayıların `M` soneki, bir sabitin `decimal` türünü kullanması gerektiğini gösterir.

Ondalık türü kullanan matematik, ondalık noktanın sağında daha fazla basamağa sahip olduğuna dikkat edin.

***Sına***

Farklı sayısal türleri gördüğünüze göre, yarıçapı 2,50 santimetre olan bir dairenin alanını hesaplayan bir kod yazın. Bir daire alanının, Radius ile çarpıldığı bir daire olduğunu unutmayın. Bir ipucu: .NET, bu değer için kullanabileceğiniz PI, <xref:System.Math.PI?displayProperty=nameWithType> için bir sabit içerir.

19 ila 20 arasında bir yanıt almanız gerekir.
[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) yanıtınızı kontrol edebilirsiniz

İsterseniz başka formüller de deneyin.

"Numaraları C#" hızlı başlangıç adımlarını tamamladınız. Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.

Aşağıdaki konularda, içindeki C# numaralar hakkında daha fazla bilgi edinebilirsiniz:

- [Integral sayısal türleri](../../language-reference/builtin-types/integral-numeric-types.md)
- [Kayan nokta sayısal türleri](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md)
