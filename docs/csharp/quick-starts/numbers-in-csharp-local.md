---
title: C# Öğreticisi - C# yerel quickstarts numaraları
description: C# sayısal türler, özellikleri ve yöntemleri keşfetme öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 6570693ea09ca2b548615291ba4f2b69f6d92482
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="numbers-in-c-quickstart"></a>C# hızlı başlangıç numaraları

Bu hızlı başlangıç C# sayı türleri hakkında etkileşimli olarak öğretilmektedir. Küçük miktarda kod yazacaksınız sonra derlemek ve bu kodu çalıştırmak. Hızlı bir dizi numaraları ve C# matematik işlemleri keşfedin dersleri içerir. Bu derslerin C# dil temelleri öğretir.

Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir. Hızlı bir genel bakış kullandığınız komutların bulunduğu [yerel quickstarts giriş](local-environment.md) daha fazla bilgi için bağlantılar ile birlikte.

## <a name="explore-integer-math"></a>Tamsayı matematik keşfedin

Adlı bir dizin oluşturun **numaraları Hızlı Başlangıç**. Geçerli dizin çalıştırma yapıp `dotnet new console -n NumbersInCSharp -o .`.

Açık **Program.cs** sık kullanılan Düzenleyicisi ve Değiştir satır `Console.Writeline("Hello World!");` aşağıdaki:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Bu kodu yazarak çalıştırmak `dotnet run` , komut penceresinde. 

Temel matematik işlemlerden tamsayılı yalnızca gördünüz. `int` Yazın gösteren bir **tamsayı**, pozitif veya negatif bir tam sayı. Kullandığınız `+` toplama simgesi. Diğer yaygın matematiksel işlemler tamsayılar şunlardır:

- `-` için çıkarma
- `*` çarpma için
- `/` bölme için

Bu farklı işlemler inceleyerek başlayın. Bu satırlar değerini yazan satırı sonra ekleyin `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Bu kodu yazarak çalıştırmak `dotnet run` , komut penceresinde. 
    
İsterseniz aynı satırda, birden çok matematik işlemleri gerçekleştirerek de deneyebilirsiniz. Deneyin `c = a + b - 12 * 17;` örneğin. Değişkenleri ve sabit sayıları karıştırma izin verilir.

> [!TIP]
> C# (veya herhangi bir programlama dili) keşfetmenizde kodu yazarken hataları hale getireceğiz. **Derleyici** bu hatalarını bulmak ve bunları sizin için rapor. Çıktı, hata iletileri içerdiğinde, örnek kod ve düzeltmek görmek için pencerenizde kodu yakından bakın.
> Bu alıştırmada, C# kod yapısını öğrenmenize yardımcı olur.     

İlk adım tamamladınız. Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın. Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır. Yeniden Adlandır, `Main` yönteme `WorkingWithIntegers` ve yeni bir yazma `Main` çağıran yöntemi `WorkingWithIntegers`. İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:

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

## <a name="explore-order-of-operations"></a>İşlem sırası keşfedin

Açıklama çağrısı çıkışı `WorkingWithIntegers()`. Bu bölümde çalışırken daha az kalabalık çıkış yapar:

```csharp
//WorkingWithIntegers();
```

`//` Başlayan bir **açıklama** C#. Kaynak kodunuz tutmak ancak kodu olarak yürütmeme istediğiniz herhangi bir metin açıklamalardır. Derleyici herhangi bir yürütülebilir kod açıklamalardan oluşturmaz.

C# dili kurallarla matematik içinde öğrenilen kurallarıyla tutarlı farklı matematik işlemlerinin önceliği tanımlar.
Çarpma ve bölme toplama ve çıkarma daha önceliklidir.
Aşağıdaki kodu ekleyerek keşfetmek, `Main` yöntemi ve execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

Çıktı çarpma toplamadan önce gerçekleştirildiğini gösterir.

İşlemi parantezler ekleyerek, farklı bir işlem sırasını zorlayabilirsiniz veya istediğiniz işlemler önce gerçekleşir. Aşağıdaki satırları ekleyin ve yeniden çalıştırın:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Birden çok sayıda farklı işlemler birleştirerek keşfedin. Aşağıdaki satırları şöyle sonuna ekleyin, `Main` yöntemi. Deneyin `dotnet run` yeniden.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Tamsayıları için ilginç bir davranıştır fark etmiş olabilirsiniz. Bir ondalık veya kesir bölümünü eklemek için sonuç bile beklediğiniz zaman tamsayı bölme her zaman bir tamsayı sonuç üretir.

Bu davranış görmediyseniz, sonuna aşağıdaki kod deneyin, `Main` yöntemi:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Tür `dotnet run` yeniden sonuçları görüntüleyin.

Devam etmeden önce bu bölümde yazılmış ve yeni bir yöntemi put tüm kod atalım. Bu yeni yöntem çağrısı `OrderPrecedence`.
Aşağıdakine benzer şunun:

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

## <a name="explore-integer-precision-and-limits"></a>Tamsayı duyarlık ve sınırları keşfedin
Bu son örnekten tamsayı bölme sonucu kesen gösterdi.
Alma **kalan** kullanarak **modulo** işleci, `%` karakter. Aşağıdaki kodda deneyin, `Main` yöntemi:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# tamsayı türü başka bir şekilde matematiksel tamsayılar farklıdır: `int` türüne sahip minimum ve maksimum sınırlar. Bu kodu ekleyin, `Main` yöntemi bu sınırları görmek için:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Bir hesaplama bu sınırlarını aşıyor bir değer oluşturursa, sahip olduğunuz bir **underflow** veya **taşma** koşulu. Diğer bir sınırının sarmalamak için yanıt görünür. Bu iki satır ekleyin, `Main` yöntemi bir örnek görmek için:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Yanıt çok düşük (negatif) tamsayı yakın olduğuna dikkat edin. Aynı olan `min + 2`. Ek işlemi **taştı** tamsayı izin verilen değerleri.
Taşma "geçici en büyük olası tamsayı değerini küçüğe sarmalar" yanıt çok büyük negatif bir sayı nedeni.

Diğer sayısal türler farklı sınırlar ve ne zaman kullanacağınız duyarlık vardır `int` türü gereksinimlerinizi karşılayacak değil. Bu sonraki inceleyelim.

Bir kez daha, bu bölümde ayrı bir yöntem içine yazdığınız kodun şimdi taşıyın. Bu ad `TestLimits`. 

## <a name="work-with-the-double-type"></a>Çift tür ile çalışma

`double` Sayısal tür çift duyarlıklı kayan noktalı sayıyı temsil eder. Bu koşullar, yeni olabilir. A **kayan nokta** sayıdır çok büyük veya küçük büyüklüğü integral olmayan sayılar temsil etmek kullanışlıdır. **Çift duyarlıklı** daha büyük duyarlık kullanılarak bu sayı depolanır anlamına gelir **tek duyarlıklı**. Modern bilgisayarlarda tek duyarlıklı sayılar daha çift duyarlıklı kullanmak için daha yaygın bir durumdur.
İnceleyelim. Aşağıdaki kodu ekleyin ve sonucu bakın:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Yanıt sayının ondalık kısmı içerdiğine dikkat edin. Double biraz daha karmaşık bir ifadesiyle deneyin:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

Bir çift değer aralığını tamsayı değerleri çok daha fazladır. Şu ana kadar yazdıklarınızı altına aşağıdaki kodu deneyin:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Bu değerleri bilimsel gösterimde yazdırılır. Sol tarafındaki sayıya `E` significand değil. Sağa üs 10 gücünü sayıdır. 

Yalnızca ondalık sayı gibi olarak matematik hataları yuvarlama çiftleri C# olabilir. Bu kod deneyin:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Bunu biliyor `0.3` yinelenen tam olarak aynı olup `1/3`.

***Challenge***

Büyük sayılar, küçük sayılar, çarpma ve bölme kullanarak diğer hesaplamalarla deneyin `double` türü.  Daha karmaşık hesaplamalar deneyin.

Sınama ile biraz zaman harcanan sonra yazdıktan ve yeni bir yöntemi yerleştirin kod alın. Bu yeni yöntem adı `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Sabit noktası türleri ile çalışma

C# temel sayısal türler gördünüz: tamsayılar ve iki katına çıkar.  Bilgi edinmek için bir tür: `decimal` türü. `decimal` Türüne sahip daha küçük bir aralık daha iyi kesinlik ancak `double`. Terim **sabit noktası** ondalık (veya ikili noktası) taşınmaz anlamına gelir. Bir göz atalım:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Aralık değerinden küçük olduğunu fark `double` türü. Aşağıdaki kod deneyerek decimal türü ile daha iyi kesinlik görebilirsiniz:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

`M` Numaraları sonekidir nasıl bir sabit kullanması gerektiğini belirtmek `decimal` türü.

Decimal türü kullanarak matematik ondalık konumun sağında daha fazla basamağa sahip olmadığına dikkat edin. 

***Challenge***

Farklı sayısal türler gördüğünüze göre 2.50 santimetreden, RADIUS olduğu dairenin alanı hesaplar kod yazın. Unutmayın PI ile çarpılmış dairenin alanı kare RADIUS olduğunu. Bir ipucu: .NET PI için bir sabit içeriyor <xref:System.Math.PI?displayProperty=nameWithType> , bu değer için kullanabilirsiniz. 

19 ve 20 arasında bir yanıt almanız gerekir.
Yanıtınız tarafından kontrol edebilirsiniz [Github'da tamamlanmış örnek kodu incelemeden](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)

İsterseniz başka bir formüller deneyin. 

"Numaraları C# ' ta" Hızlı Başlangıç tamamladınız. İle devam edebilirsiniz [dallar ve döngüler](branches-and-loops-local.md) kendi geliştirme ortamında hızlı başlangıç.

Aşağıdaki konularda C# numaraları hakkında daha fazla bilgi edinebilirsiniz:

[Tam sayı türleri tablosu](../language-reference/keywords/integral-types-table.md)   
[Kayan nokta türleri tablosu](../language-reference/keywords/floating-point-types-table.md)   
[Yerleşik türler tablosu](../language-reference/keywords/built-in-types-table.md)   
[Örtük sayısal dönüşümler tablosu](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Açık Sayısal Dönüştürmeler Tablosu](../language-reference/keywords/explicit-numeric-conversions-table.md)

