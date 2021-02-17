---
title: C# dilinde sayılar-C# öğreticisine giriş
description: Sayısal türleri, kullanımları, özellikleri ve yöntemleri inceleyerek C# hakkında bilgi edinin.
ms.date: 02/05/2021
ms.openlocfilehash: 5576827cc92842a2cbd5374a691d9a5c560aec25
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100626806"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>C 'de integral ve kayan nokta numaralarını işleme\#

Bu öğretici, C# ' deki sayısal türleri etkileşimli olarak size öğretir. Küçük miktarlarda kod yazacaksınız, daha sonra bu kodu derleyip çalıştıracaksınız. Öğretici, C# ' de sayıları ve matematik işlemlerini keşfetmenizi sağlayan bir dizi ders içerir. Bu dersler size C# dilinin temel özelliklerini öğretir.

## <a name="prerequisites"></a>Önkoşullar

Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler. Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz. Mac veya Windows üzerinde Visual Studio 2019 ' i kullanabilirsiniz. Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](local-environment.md).

## <a name="explore-integer-math"></a>Tamsayı matematiğini inceleme

Sayı adlı bir dizin oluşturun *-hızlı başlangıç*. Geçerli dizin yapın ve şu komutu çalıştırın:

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

En sevdiğiniz düzenleyicide *program.cs* açın ve dosyanın içeriğini aşağıdaki kodla değiştirin:

```csharp
using System;

int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Komut pencerenizi yazarak bu kodu çalıştırın `dotnet run` .

Tamsayılarla temel matematik işlemlerinden birini gördünüz. `int`Tür bir **tamsayıyı**, sıfır, pozitif veya negatif bir tam sayıyı temsil eder. Toplama için `+` sembolünü kullanırsınız. Tamsayılar için sıklıkla kullanılan diğer matematiksel işlemler şunlardır:

- çıkarma için `-`
- çarpma için `*`
- bölme için `/`

Bu farklı işlemleri keşfederek başlayın. Değerini yazan satırdan sonra bu satırları ekleyin `c` :

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

Komut pencerenizi yazarak bu kodu çalıştırın `dotnet run` .

Ayrıca, isterseniz aynı satırda birden çok matematik işlemi yazarak da deneyebilirsiniz. Örneğin, deneyin `c = a + b - 12 * 17;` . Değişkenlerin ve sabit sayıların karıştırılmasına izin verilir.

> [!TIP]
> C# dilini (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. **Derleyici** bu hataları bulup size bildirir. Hata mesajları içerdiğinde, nelerin düzeltileceğini görmek için örnek koda ve penceredeki koda yakından bakın. Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.

İlk adımı tamamladınız. Sonraki bölüme başlamadan önce geçerli kodu ayrı bir *yönteme* taşıyalim. Bir yöntem, birlikte gruplanmış ve bir ad verilen deyimler dizisidir. Yöntemi, ardından yönteminin adını yazarak çağırabilirsiniz `()` . Kodunuzun yöntemlere düzenlenmesi, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:

```csharp
using System;

WorkWithIntegers();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
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
```

Satırı `WorkWithIntegers();` yöntemini çağırır. Aşağıdaki kod yöntemini bildirir ve tanımlar.

## <a name="explore-order-of-operations"></a>İşlem sırasını inceleme

Çağrısını not edin `WorkingWithIntegers()` . Bu bölümde çalışırken çıktının daha az karışık hale gelir:

```csharp
//WorkWithIntegers();
```

`//`C# dilinde bir **Açıklama** başlatır. Açıklamalar, kaynak kodunuzda tutmak istediğiniz tüm metinlerdir, ancak kod olarak yürütülmez. Derleyici açıklamalardan herhangi bir yürütülebilir kod oluşturmaz. `WorkWithIntegers()`Bir yöntem olduğundan, yalnızca bir satır için açıklama yazmanız gerekir.

C# dili, farklı matematik işlemlerinin önceliğini matematikte öğrendiğiniz kurallarla tutarlı bir şekilde tanımlar. Çarpma ve bölme işlemleri, toplama ve çıkarma işlemlerinden önce gelir. ' I çağırarak ve yürüttükten sonra aşağıdaki kodu ekleyerek bunu keşfedebilirsiniz `WorkWithIntegers()` `dotnet run` :

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

Birçok farklı işlemi birleştirerek daha fazlasını keşfedin. Aşağıdaki satırlara benzer bir şey ekleyin. `dotnet run` komutunu yeniden deneyin.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Tamsayılar için farklı bir davranışla karşılaşmış olabilirsiniz. Sonucun ondalık veya kesir bölümü içermesini bekliyor olsanız da tamsayı bölme işlemi her zaman tamsayı sonucu verir.

Bu davranışı görmediyseniz, aşağıdaki kodu deneyin:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

`dotnet run`Sonuçları görmek için yeniden yazın.

' In üzerine geçmeden önce, bu bölümde yazdığınız tüm kodu alıp yeni bir yönteme koyabilirsiniz. Bu yeni yöntemi çağırın `OrderPrecedence` . Kodunuz şuna benzemelidir:

```csharp
using System;

// WorkWithIntegers();
OrderPrecedence();

void WorkWithIntegers()
{
    int a = 18;
    int b = 6;
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

void OrderPrecedence()
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
    int h = (e + f) / g;
    Console.WriteLine(h);
}
```

## <a name="explore-integer-precision-and-limits"></a>Tamsayı duyarlığını ve sınırlarını inceleme

Son örnek, tamsayı bölme işleminin sonucu kestiğini size göstermiştir. **Geri kalanını** , **mod** işleci, karakterini kullanarak edinebilirsiniz `%` . Yöntem çağrısından sonra aşağıdaki kodu deneyin `OrderPrecedence()` :

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır. Bu sınırları görmek için bu kodu ekleyin:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Bir hesaplama, bu sınırları aşan bir değer veriyorsa bu, **aşağı taşma** veya **taşma** koşulunuzun olduğu anlamına gelir. Yanıtın bir sınırdan diğerine kaydığı görülüyor. Örnek görmek için bu iki satırı ekleyin:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Yanıtın tam sayı alt sınırına (negatif) oldukça yakın olduğuna dikkat edin. Bu, `min + 2` ile aynıdır. Toplama işlemi, tamsayılar için izin verilen değerleri **aşmıştır**. Taşma durumu en büyük olası tamsayı değerinden en küçük olana "kaydığından" yanıt oldukça büyük bir negatif sayıdır.

`int` türü, gereksinimlerinizi karşılamadığında kullanabileceğiniz farklı sınırlar ve duyarlık içeren başka sayısal türler de mevcuttur. Daha sonra bu diğer türleri keşfedelim. Sonraki bölüme başlamadan önce, bu bölümde yazdığınız kodu ayrı bir yönteme taşıyın. Bunu, `TestLimits` olarak adlandırın.

## <a name="work-with-the-double-type"></a>Çift tür ile çalışma

`double` sayısal türü, çift duyarlıklı kayan noktalı bir sayıyı ifade eder. Bu terimler sizin için yeni olabilir. **Kayan noktalı** sayı, büyüklük açısından oldukça büyük veya küçük olabilen, tamsayı olmayan değerleri ifade etmek için kullanılır. **Çift duyarlık** , değeri depolamak için kullanılan ikili basamak sayısını açıklayan göreli bir terimdir. **Çift duyarlık** sayıları, ikili basamakların sayısının **tek duyarlıklı** olarak iki katına sahiptir. Modern bilgisayarlarda, tek duyarlık sayılarıyla çift duyarlık kullanmak daha yaygındır. **Tek duyarlık** numaraları anahtar sözcüğü kullanılarak belirtilir `float` . İnceleyelim mi? Aşağıdaki kodu ekleyin ve sonucu görüntüleyin:

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

Bu değerler bilimsel gösterimde yazdırılır. `E` değerinin sol tarafındaki sayı katsayıdır. Sağ taraftaki sayı 10’un bir kuvveti olarak üstür. Matematikteki ondalık sayılar gibi C# dilindeki çift değerlerde de yuvarlama hataları olabilir. Şu kodu deneyin:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

`0.3`Yinelenen tam olarak aynı olmadığını bilirsiniz `1/3` .

***Sınama***

Türü kullanarak büyük sayılar, küçük sayılar, çarpma ve bölme ile diğer hesaplamaları deneyin `double` . Daha karmaşık hesaplamalar deneyin. Zorluğa bir süre harcadıktan sonra yazdığınız kodu alın ve yeni bir yönteme yerleştirin. Yeni yönteme adlandırın `WorkWithDoubles` .

## <a name="work-with-decimal-types"></a>Ondalık türlerle çalışma

C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler. Öğreneceğinizi öğrenmek için başka bir tür vardır: `decimal` türü. `decimal` türü, `double` türünden daha küçük bir aralığa ancak daha fazla duyarlığa sahiptir. Şimdi buna bir göz atalım:

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

Sayılardaki `M` sonekiyle, bir sabit sayının `decimal` türünü nasıl kullanması gerektiğini belirtirsiniz. Aksi takdirde, derleyici türü varsayar `double` .

> [!NOTE]
> Harf, `M` `double` ve anahtar kelimeleri arasında en görsel olarak ayrı bir harf olarak seçilmiştir `decimal` .

Ondalık türünün kullanıldığı matematikte, ondalık ayırıcının sağ tarafında daha fazla basamak bulunduğunu görebilirsiniz.

***Sınama***

Farklı sayısal türleri gördüğünüze göre yarı çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın. Bir dairenin alanının, yarı çapın karesinin PI sayısı ile çarpımından elde edildiğini unutmayın. İpucu: .NET, PI sayısı için kullanabileceğiniz <xref:System.Math.PI?displayProperty=nameWithType> sabit değerini içerir. <xref:System.Math.PI?displayProperty=nameWithType>, ad alanında belirtilen tüm sabitler gibi `System.Math` bir `double` değerdir. Bu nedenle, `double` `decimal` Bu zorluk için değer yerine kullanmanız gerekir.

19 ile 20 arasında bir yanıt almanız gerekir. [GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)yanıtınızı kontrol edebilirsiniz.

Dilerseniz diğer formüllerden de deneme yapabilirsiniz.

"C# dilinde sayılar" hızlı başlangıç adımlarını tamamladınız. Kendi geliştirme ortamınızda [dallar ve döngüler](branches-and-loops-local.md) hızlı başlangıç ile devam edebilirsiniz.

Aşağıdaki makalelerde C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:

- [Tamsayı sayısal türler](../../language-reference/builtin-types/integral-numeric-types.md)
- [Kayan nokta sayısal türleri](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md)
