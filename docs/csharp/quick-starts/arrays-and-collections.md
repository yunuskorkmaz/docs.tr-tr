---
title: "Hızlı Başlangıç - koleksiyonlar - C# Kılavuzu"
description: "C# bu hızlı başlangıç listesi koleksiyonunda inceleyerek öğrenin."
keywords: "C#, Get Started, öğretici, koleksiyonları listesi"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 228a9dd88d0a511492ccb8b70e0231278969acbe
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2017
---
# <a name="c-quick-start-collections"></a>C# hızlı başlangıç: koleksiyonları #

Bu hızlı başlangıç C# dili ve temel bilgileri tanıtılmaktadır <xref:System.Collections.Generic.List%601> sınıfı.

Bu hızlı başlangıç geliştirme için kullanabileceğiniz bir makine olmasını bekler. .NET konu [Get Started 10 dakika içinde](https://www.microsoft.com/net/core) Mac, PC ya da Linux yerel geliştirme ortamınızı ayarlamak için yönergeler içerir.

## <a name="a-basic-list-example"></a>Basit liste örnek.

Adlı bir dizin oluşturun **listesi Hızlı Başlangıç**. Geçerli dizin çalıştırma yapıp `dotnet new console`.

> [!NOTE]
> Yalnızca tamamladıysanız [10 dakika içinde .NET ile çalışmaya başlama](https://www.microsoft.com/net), az önce oluşturduğunuz Uygulamam uygulamayı kullanmaya devam.
 
Açık **Program.cs** sık kullanılan Düzenleyicisi ve var olan kodu aşağıdakilerle değiştirin:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

Değiştir `<name>` adıyla. Kaydet **Program.cs**. Tür `dotnet run` , konsol penceresinde deneyin.

Yalnızca dizelerinin listesini oluşturduğunuz, üç adları bu listeye eklenen ve tümü büyük harf adlarında çıkışı yazdırılmıştır. Listede ilerleyin döngü içinde daha önce hızlı başlatır, öğrendiğinize kavramları kullanıyorsunuz.

Adlarını görüntülemek için kod kullanır **Ara değerli dizeler**.  Öncesinde ne zaman bir `string` ile `$` karakter dizesi bildiriminde C# kodu katıştırmak. Gerçek dize, C# kodu ürettiği değeri ile değiştirir. Bu örnekte, yerini `{name.ToUpper()}` aradığınız çünkü her adıyla dönüştürülen büyük harfler için <xref:System.String.ToUpper%2A> yöntemi.

Şimdi keşfetme tutun.
    
## <a name="modify-list-contents"></a>Liste içeriklerini değiştirme

Kullandığı oluşturduğunuz koleksiyonda <xref:System.Collections.Generic.List%601> türü. Bu tür, öğelerin sıralarının depolar. Açılı ayraçları arasında öğelerin türü belirtin.
    
Bu önemli bir özelliği <xref:System.Collections.Generic.List%601> türüdür onu büyütür veya böylelikle küçültür, ekleme veya öğeleri kaldırma olanak sağlar. Bu kodu kapatmadan önce ekleyin `}` içinde `Main` yöntemi:

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

İki daha fazla ad listesinin sonuna ekledik. Ayrıca bir de kaldırdınız. Dosya ve türü Kaydet `dotnet run` denemek üzere.
    
<xref:System.Collections.Generic.List%601> Tarafından ayrı öğeleri başvuru sağlar **dizin** de. Dizin arasında yerleştirin `[` ve `]` listesi adından belirteçleri. C# 0 ilk dizini kullanır. Bu kodu eklediğiniz kodun hemen altına ekleyin ve deneyin:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Bir dizin listesi ötesinde erişemiyor. Bu nedenle en büyük geçerli dizin biridir dizinlerini 0'da, başlangıç unutmayın listedeki öğeleri sayısından küçük. Ne kadar süreyle listeyi kullanarak denetleyebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> özelliği. Main yönteminin sonuna aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Dosya ve türü Kaydet `dotnet run` yeniden sonuçları görüntüleyin.    

## <a name="search-and-sort-lists"></a>Arama ve sıralama listeler
Bizim örneklerimizi görece küçük listeleri kullanın, ancak uygulamalarınızı genellikle bazen binlerce numaralandırma pek çok daha fazla öğe ile listeleri oluşturabilirsiniz. Bu büyük koleksiyonlarda öğeleri bulmak için farklı öğeleri listede arama gerekir. <xref:System.Collections.Generic.List%601.IndexOf%2A> Yöntemi için bir öğe arar ve öğenin dizinini döndürür. Bu kodu altına ekleyin, `Main` yöntemi:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
    
}
```

Listenizdeki öğeleri de sıralanabilir. <xref:System.Collections.Generic.List%601.Sort%2A> Yöntemi (alfabetik olarak söz konusu olduğunda dizeleri) normal sıralarına listesindeki tüm öğeleri sıralar. Bu kodu altına ekleyin bizim `Main` yöntemi:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Dosyayı kaydedip türü `dotnet run` bu en son sürümünü denemek için.

Şimdi, sonraki bölüme başlamadan önce geçerli kod ayrı bir yöntem taşıyın. Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır. Yeniden Adlandır, `Main` yönteme `WorkingWithStrings` ve yeni bir yazma `Main` çağıran yöntemi `WorkingWithStrings`. İşiniz bittiğinde, kodunuzu aşağıdaki gibi görünmelidir:

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a>Diğer türleri listesi

Kullanmakta olduğunuz `string` kadarki listelerindeki türü. Olalım bir <xref:System.Collections.Generic.List%601> farklı türü kullanıyor. Şimdi bir sayı kümesi oluşturun. 

Aşağıdaki yeni altına ekleyin `Main` yöntemi:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Tamsayı listesi oluşturur ve ilk iki tamsayı 1 değerine ayarlar. İlk iki değerlerini bunlar bir *Fibonacci dizisi*, sayılardan oluşan bir dizi. Sonraki her Fibonacci numarası, önceki iki sayı toplamı gerçekleştirerek bulunur. Bu kodu ekleyin:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Dosyayı kaydedip türü `dotnet run` sonuçları görüntüleyin. 

> [!TIP]
> Bu bölüm yalnızca yoğunlaşmak için çağıran kodu yorum yapabileceği `WorkingWithStrings();`. Yalnızca iki put `/` bu gibi karakterler çağrı önünde: `// WorkingWithStrings();`. 

## <a name="challenge"></a>sınama
Birlikte koyabilirsiniz, bkz: Bu ve önceki sürümleri dersleri bazıları dersleri. Ne kadar Fibonacci numaralarıyla derlediğiniz genişletin. Deneyin ve ilk 20 numaralarını sırayla oluşturması için kod yazın.

## <a name="complete-challenge"></a>Tam sınama

Örnek bir çözüm tarafından görebilirsiniz [Github'da tamamlanmış örnek kodu incelemeden](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)

Her döngü tekrarında ile son iki tamsayı listesinde, bunları birleşimi ve bu değer listesine ekleyerek yönlendiriyoruz. Listeye 20 öğeleri ekleyene kadar döngü tekrarlar.

Tebrikler, liste hızlı başlangıç tamamladınız. İle devam edebilirsiniz [sınıfları giriş](introduction-to-classes.md) kendi geliştirme ortamında hızlı başlangıç.

İle çalışma hakkında daha fazla bilgiyi `List` yazın [.NET Kılavuzu](../../standard/index.md) konuyla ilgili [koleksiyonları](../../standard/collections/index.md). Ayrıca diğer birçok koleksiyon türleri hakkında bilgi edineceksiniz.
