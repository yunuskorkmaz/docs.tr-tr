---
title: C# C#
description: Sayısal C# türleri, özelliklerini ve yöntemlerini inceleyerek bilgi edinin.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 436e8db10f973b468458987150e1312a16103b91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850685"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>C 'de integral ve kayan nokta numaralarını işleme\#

Bu öğretici, size etkileşimli olarak C# sayısal türler öğretir. Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız. Öğreticide, içindeki C#sayıları ve matematik işlemlerini keşfettiği bir dizi ders bulunur. Bu dersler, C# dilin temellerini öğretir.

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, yerel geliştirme ortamınızı Mac, PC veya Linux üzerinde ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı için bağlantılarla birlikte [geliştirme araçları hakkında bilgi sahibi olmaya gelmiştir](local-environment.md) .

## <a name="explore-integer-math"></a>Tamsayı matematiğini keşfet

Sayı adlı bir dizin oluşturun **-hızlı başlangıç**. Geçerli dizini oluşturun ve çalıştırın `dotnet new console -n NumbersInCSharp -o .`.

En sevdiğiniz düzenleyicide **program.cs** açın ve satırı `Console.WriteLine("Hello World!");` aşağıdaki ile değiştirin:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Komut pencerenizi yazarak `dotnet run` bu kodu çalıştırın.

Yalnızca tamsayılarla temel matematik işlemlerinden birini gördünüz. Tür bir tamsayıyı, pozitif veya negatif bir tam sayıyı temsil eder. `int` Eklemek için `+` simgesini kullanın. Tamsayılar için diğer yaygın matematik işlemleri şunlardır:

- `-`çıkarma için
- `*`Çarpma için
- `/`Bölüm için

Bu farklı işlemleri inceleyerek başlayın. Değerini yazan satırdan sonra bu satırları ekleyin `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Komut pencerenizi yazarak `dotnet run` bu kodu çalıştırın.

İsterseniz aynı satırda birden çok matematik işlemi gerçekleştirerek da deneyebilirsiniz. Örneğin `c = a + b - 12 * 17;` , deneyin. Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.

> [!TIP]
> Keşfederken C# (veya herhangi bir programlama dilini), kod yazarken hata oluşturursunuz. **Derleyici** bu hataları bulacak ve size rapor eder. Çıktı hata iletileri içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın.
> Bu alıştırma, C# kod yapısını öğrenmenize yardımcı olur.

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. Yönteminizi olarak `WorkingWithIntegers` yeniden adlandırın ve çağıran `Main` `WorkingWithIntegers`yeni bir yöntem yazın. `Main` İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

Çağrısını not edin `WorkingWithIntegers()`. Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//WorkingWithIntegers();
```

, `//` İçinde C#bir **yorum** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz.

C# Dil, matematiksel olarak öğrendiğiniz kurallarla tutarlı kurallara sahip farklı matematik işlemlerinin önceliğini tanımlar.
Çarpma ve bölme, toplama ve çıkarma konusunda önceliklidir.
`Main` Yöntemine aşağıdaki kodu ekleyerek ve yürüterek `dotnet run`şunu araştırın:

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
d = (a  + b) * c;
Console.WriteLine(d);
```

Birçok farklı işlemi birleştirerek daha fazlasını keşfedebilirsiniz. `Main` Yönteminizin en altında aşağıdaki satırlara benzer bir şey ekleyin. Yeniden `dotnet run` deneyin.

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
int h = (e  + f) / g;
Console.WriteLine(h);
```

Sonuçları `dotnet run` görmek için yeniden yazın.

' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz. Bu yeni yöntemi `OrderPrecedence`çağırın.
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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

            d = (a  + b) * c;
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
**Geri kalanını** , **mod** `%` işleci, karakterini kullanarak edinebilirsiniz. Yönteyinizdeki `Main` aşağıdaki kodu deneyin:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# Tamsayı türü matematik tamlarından farklı bir şekilde farklılık gösterir: `int` türün en az ve en fazla sınırı vardır. Bu sınırları görmek için bu `Main` kodu yönteminizin içine ekleyin:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Hesaplama bu sınırları aşan bir değer üretirse, bir **yetersiz** yer veya **taşma** koşulunuz vardır. Yanıt bir sınırdan diğerine kaydırılır. Bir örnek görmek için bu iki `Main` satırı yönteminizin içine ekleyin:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Yanıtın en düşük (negatif) tamsayıya çok yakın olduğuna dikkat edin. Bu, ile `min + 2`aynıdır.
Toplama işlemi, tamsayılar için izin verilen değerleri **taşırdı** .
Bir taşma, olası en büyük tamsayı değerinden en küçüğe "kaydırdığı için, yanıt çok büyük negatif bir sayıdır.

`int` Türü gereksinimlerinizi karşılamıyorsa, farklı sınırlara ve duyarlığa sahip başka sayısal türler vardır. Bundan sonra bu ileri keşfedelim.

Bir kez daha, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyalim. `TestLimits`Adlandırın.

## <a name="work-with-the-double-type"></a>Double türüyle çalışma

`double` Sayısal tür bir çift duyarlıklı kayan noktalı sayıyı temsil eder. Bu terimler sizin için yeni olabilir. **Kayan noktalı** sayı, çok büyük veya küçük olabilecek tamsayı olmayan sayıları temsil etmek için kullanışlıdır. **Çift duyarlıklı** , bu sayıların **tek duyarlığa**göre daha fazla duyarlık kullanılarak depolandığı anlamına gelir. Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır.
Keşfedelim. Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Yanıtın, bölümün ondalık kısmını içerdiğine dikkat edin. Double değerleri ile biraz daha karmaşık bir ifade deneyin:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Double değerinin aralığı tamsayı değerlerinden çok daha büyüktür. Şu ana kadar yazdıklarınız için aşağıdaki kodu deneyin:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Bu değerler bilimsel gösterimde yazdırılır. Öğesinin solundaki sayı mantisinin ' `E` dir. Sağdaki sayı, 10 ' un üssü olarak üs değeri olan sayıdır.

Matematiği gibi ondalık sayılar gibi, içindeki Double C# değerleri de yuvarlama hataları içerebilir. Şu kodu deneyin:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

`0.3` Tekrarda tam olarak `1/3`aynı olmadığını bilirsiniz.

***Sına***

`double` Türü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin.  Daha karmaşık hesaplamalar deneyin.

Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin. Yeni yönteme `WorkWithDoubles`adlandırın.

## <a name="work-with-fixed-point-types"></a>Sabit nokta türleriyle çalışma

Temel sayısal türleri C#: tamsayılar ve Double değerleri ile gördünüz.  Öğreneceğinizi bir başka tür vardır: `decimal` türü. Türün daha küçük bir aralığı, ancak daha fazla `double`duyarlık vardır. `decimal` **Sabit nokta** terimi, ondalık noktanın (veya ikili noktanın) taşınmayacağı anlamına gelir. Bir göz atalım:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Aralığın `double` türden küçük olduğuna dikkat edin. Aşağıdaki kodu deneyerek ondalık türüyle daha büyük duyarlık görebilirsiniz:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

Sayıların son eki, bir sabitin `decimal` türü kullanması gerektiğini gösterir. `M`

Ondalık türü kullanan matematik, ondalık noktanın sağında daha fazla basamağa sahip olduğuna dikkat edin.

***Sına***

Farklı sayısal türleri gördüğünüze göre, yarıçapı 2,50 santimetre olan bir dairenin alanını hesaplayan bir kod yazın. Bir daire alanının, Radius ile çarpıldığı bir daire olduğunu unutmayın. Bir ipucu: .net, <xref:System.Math.PI?displayProperty=nameWithType> bu değer için kullanabileceğiniz PI için bir sabit içerir.

19 ila 20 arasında bir yanıt almanız gerekir.
[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) yanıtınızı kontrol edebilirsiniz

İsterseniz başka formüller de deneyin.

"Numaraları C#" hızlı başlangıç adımlarını tamamladınız. Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.

Aşağıdaki konularda, içindeki C# numaralar hakkında daha fazla bilgi edinebilirsiniz:

- [Integral türleri](../../language-reference/builtin-types/integral-numeric-types.md)
- [Kayan Nokta Türleri Tablosu](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Yerleşik Türler Tablosu](../../language-reference/keywords/built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](../../language-reference/keywords/explicit-numeric-conversions-table.md)
