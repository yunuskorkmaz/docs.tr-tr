---
title: İçindeki numaralandırır C# -giriş C# Öğreticisi
description: Bilgi C# sayısal türler, özellikler ve yöntemler keşfetmeye tarafından.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 52feb91fc011902f1e30f6b747512a7e0908bfbf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197463"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>İntegral ve kayan nokta numaraları ile düzenlemeC# #

Bu öğretici sayısal türlerle ilgili öğretir C# etkileşimli olarak. Az miktarda kod yazacaksınız ve ardından derleyin ve kod çalıştırması. Öğreticiyi dersler ve içinde matematik işlemlerini inceleyen bir dizi içeren C#. Bu dersler size C# dilinin temellerini öğretin.

Bu öğretici geliştirme için kullanabileceğiniz bir makine olmasını bekliyor. .NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md) daha ayrıntılı bilgi için bağlantılarla birlikte.

## <a name="explore-integer-math"></a>Tamsayı matematiğini İnceleme

Adlı bir dizin oluşturmak **numaraları-quickstart**. Geçerli dizin ve çalışma olun `dotnet new console -n NumbersInCSharp -o .`.

Açık **Program.cs** satırı değiştirin ve tercih ettiğiniz düzenleyiciyi `Console.Writeline("Hello World!");` aşağıdaki:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Bu kod yazarak çalıştırın `dotnet run` komut pencerenizde. 

Az önce tamsayılarla gerçekleştirilen temel matematik işlemlerinden birini gördünüz. `int` Türü temsil eder bir **tamsayı**, bir pozitif veya negatif tamsayı. Kullandığınız `+` sembol ekleme. Tamsayılar için kullanılan diğer matematiksel işlemler şunlardır:

- `-` çıkarma için
- `*` çarpma için
- `/` bölme için

Bu farklı işlemleri keşfederek başlayın. Değerini yazan bir satırın sonunda şu satırı ekleyin `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Bu kod yazarak çalıştırın `dotnet run` komut pencerenizde. 
    
Dilerseniz aynı satırda birden çok matematik işlemi gerçekleştirerek de deneyebilirsiniz. Deneyin `c = a + b - 12 * 17;` örneğin. Değişkenleri ve sabit sayıları karıştırılmasına izin.

> [!TIP]
> C# (veya herhangi bir programlama dilini) keşfederken, kod yazdığınızda hatalar yapacaksınız. **Derleyici** bu hataları bulup size bildirir. Çıktı, hata iletileri içerdiğinde, örnek kod ve kodda neyin düzeltilmesi gerektiğini görmek için pencerenizi yakından bakın.
> Bu alıştırma, C# kodunun yapısını öğrenmenize yardımcı olur.     

İlk adımı tamamladınız. Sonraki bölümde başlamadan önce geçerli kodu ayrı bir yöntem geçelim. Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır. Yeniden adlandırma, `Main` yönteme `WorkingWithIntegers` ve yeni bir yazma `Main` metoduna çağrı yapan `WorkingWithIntegers`. İşiniz bittiğinde, kodunuzun şu şekilde görünmelidir:

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

## <a name="explore-order-of-operations"></a>İşlem sırasını İnceleme

Çağrı yorum `WorkingWithIntegers()`. Bu, bu bölümde çalışırken daha az dağınıktır çıkış yapar:

```csharp
//WorkingWithIntegers();
```

`//` Başlatan bir **yorum** içinde C#. Kaynak kodunuzu korumakla birlikte kod olarak yürütmeme istediğiniz herhangi bir metin açıklamaları bulunmaktadır. Derleyicinin açıklamaları herhangi bir yürütülebilir kod oluşturmaz.

C# dil kuralları Matematikte öğrendiğiniz kurallarla tutarlı farklı matematik işlemlerinin önceliğini tanımlar.
Çarpma ve bölme, toplama ve çıkarma öncelik kazanır.
Aşağıdaki kodu ekleyerek keşfedin, `Main` yöntemi ve yürütme `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Çıkış, çarpma işleminin toplama işleminden önce gerçekleştiğini gösterir.

İşlemi parantez içine ekleyerek farklı bir işlem sırasını zorlayabilirsiniz veya istediğiniz operations ilk kez gerçekleştirildi. Aşağıdaki satırları ekleyin ve yeniden çalıştırın:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Birçok farklı işlemi birleştirerek daha fazlasını keşfedin. Aşağıdaki satırları benzer bir şey alt kısmında ekleyin, `Main` yöntemi. Deneyin `dotnet run` yeniden.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Tamsayılar için ilgi çekici bir davranışı fark etmiş olabilirsiniz. Sonucun ondalık veya kesir bölümü içermesini bile beklediğiniz, Tamsayı bölme her zaman tamsayı sonucu üretir.

Bu davranışı görmediyseniz sonuna aşağıdaki kodu deneyin, `Main` yöntemi:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Tür `dotnet run` yeniden sonuçları görmek için.

Devam etmeden önce bu bölümde yazılan ve yeni bir yöntemde put tüm kod ele alalım. Bu yeni bir yöntem çağrısı `OrderPrecedence`.
Bu gibi bir şeyle görmeniz:

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

## <a name="explore-integer-precision-and-limits"></a>Tamsayı duyarlığını ve sınırlarını İnceleme
Son örnek, Tamsayı bölme sonucu kestiğini size göstermiştir.
Alabileceğiniz **kalan** kullanarak **modül** işleci `%` karakter. Aşağıdaki kodu deneyin, `Main` yöntemi:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# tamsayı türü diğer bir özelliğiyle matematiksel tamsayılardan farklıdır: `int` türünün alt ve üst sınırları vardır. Bu kodu ekleyin, `Main` yöntemi bu sınırları görmek için:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Bir hesaplama, bu sınırları aşan bir değer veriyorsa, sahip olduğunuz bir **underflow** veya **taşma** koşul. Yanıtın bir sınırdan diğerine kaydığı görünür. Bu iki satırları ekleyin, `Main` yöntemi bir örnek görmek için:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Yanıt çok az (negatif) tamsayı yakın olduğuna dikkat edin. Aynı olan `min + 2`. Toplama işlemi **taştı** tamsayılar için izin verilen değerler.
Taşma "etrafında en büyük olası tamsayı değerinden en küçük kaydırıldığı" yanıt oldukça büyük negatif bir sayı olmasıdır.

Farklı sınırlar ve ne zaman kullanacağınız duyarlık içeren başka sayısal türler vardır `int` türü, gereksinimlerinizi karşılamadığında. Bir sonraki adımda bunları inceleyelim.

Bir kez daha, bu bölümde ayrı bir yöntem içinde yazdığınız kodun geçelim. Adlandırın `TestLimits`. 

## <a name="work-with-the-double-type"></a>Çift tür ile çalışma

`double` Sayısal türü temsil eder, çift duyarlıklı kayan nokta sayısı. Bu terimler sizin için yeni olabilir. A **kayan nokta** numarası, çok büyük ya da büyüklük açısından küçük olabilen, tamsayı olmayan değerleri temsil etmek kullanışlıdır. **Çift duyarlıklı** bu numaraları daha fazla duyarlık kullanılarak depolandığı anlamına gelir **tek duyarlıklı**. Modern bilgisayarlarda çift duyarlıklı tek duyarlıklı sayılara kullanmak daha yaygındır.
Haydi keşfedelim. Aşağıdaki kodu ekleyin ve sonuca bakın:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Yanıt sayının ondalık kısmını içerdiğine dikkat edin. Çift değerlerle biraz daha karmaşık bir ifadeyi deneyin:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Çift değerin aralığı, tamsayı değerlerinden çok büyük. Şu ana kadar yazdıklarınızı altına aşağıdaki kodu deneyin:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Bu değerler bilimsel gösterimde yazdırılır. Sol tarafındaki sayı `E` katsayıdır. Sağ taraftaki sayı, 10 'un bir kuvveti üstür. 

Yalnızca ondalık sayılar gibi C# double yuvarlama hataları olabilir. Bu kodu deneyin:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Bildiğiniz `0.3` yinelenen tam olarak aynı olup `1/3`.

***Sınama***

Büyük sayılar, küçük sayılar, çarpma ve bölme kullanarak ile diğer hesaplamaları deneyin `double` türü.  Daha karmaşık hesaplamalar deneyin.

Çok süre çalışmış olduğunuz sonra kodu yazdıktan ve yeni bir yöntemde yerleştirin yararlanın. Bu yeni bir yöntem adı `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Sabit nokta türleriyle çalışma

C# dilinde temel sayısal türleri gördünüz: tamsayılar ve çiftler.  Bilgi edinmek için bir türü vardır: `decimal` türü. `decimal` Türünde daha küçük bir aralığa ancak daha fazla duyarlığa `double`. Terim **sabit nokta** Ondalık ayırıcının (veya ikili noktasının) hareket etmediği anlamına gelir. Bir göz atalım:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Aralık değerinden küçük olduğunu fark `double` türü. Aşağıdaki kodu deneyerek ondalık türünde daha fazla duyarlık görebilirsiniz:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

`M` Numaralarda sonekidir nasıl bir sabit kullanması gerektiğini belirten `decimal` türü.

Ondalık türünün kullanıldığı Matematikte, ondalık noktanın sağındaki daha fazla rakam olduğuna dikkat edin. 

***Sınama***

Farklı sayısal türleri gördüğünüze göre çapı 2,50 santimetre olan bir dairenin alanını hesaplayan kodu yazın. Unutmayın PI sayısı ile çarpılan bir dairenin alanının kare RADIUS olduğunu. İpucu: .NET, PI sayısı için bir sabit içeriyor <xref:System.Math.PI?displayProperty=nameWithType> , bu değer için kullanabilirsiniz. 

19 ile 20 arasında bir yanıt almanız gerekir.
Yanıtınız tarafından denetleyebilirsiniz [tamamlanan örnek koda Github'da bakmak](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)

Dilerseniz diğer formüllerden deneyin. 

Tamamladınız "içindeki numaralandırır C#" Hızlı Başlangıç. İle devam edebilir [dallar ve döngüler](branches-and-loops-local.md) kendi geliştirme ortamında hızlı başlangıç.

Aşağıdaki konularda C# dilinde sayılar hakkında daha fazla bilgi edinebilirsiniz:

[Tam sayı türleri tablosu](../../language-reference/keywords/integral-types-table.md)   
[Kayan nokta türleri tablosu](../../language-reference/keywords/floating-point-types-table.md)   
[Yerleşik türler tablosu](../../language-reference/keywords/built-in-types-table.md)   
[Örtük sayısal dönüşümler tablosu](../../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Açık Sayısal Dönüştürmeler Tablosu](../../language-reference/keywords/explicit-numeric-conversions-table.md)
