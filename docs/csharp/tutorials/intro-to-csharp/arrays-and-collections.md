---
title: Koleksiyonlar - giriş çalışın C# Öğreticisi
description: Bilgi C# liste koleksiyonu bu öğreticideki keşfetmeye tarafından.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 9a910ccd6265011fc0e5540b461ba089dbd3e7ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706370"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Veri koleksiyonları genel liste türünü kullanarak yönetmeyi öğrenin

Bu giriş niteliğindeki öğretici tanıtır C# dili ve temel <xref:System.Collections.Generic.List%601> sınıfı.

Bu öğretici geliştirme için kullanabileceğiniz bir makine olmasını bekliyor. .NET konu [10 dakika içinde kullanmaya başla](https://www.microsoft.com/net/core) Mac, PC veya Linux üzerinde yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullandığınız hesap komutları hızlı bir genel bakış yer [geliştirme araçları ile aşina](local-environment.md), daha fazla bilgi için bağlantılarla birlikte.

## <a name="a-basic-list-example"></a>Temel listesi örneği

Adlı bir dizin oluşturmak **liste-tutorial**. Geçerli dizin ve çalışma olun `dotnet new console`.

Açık **Program.cs** sık kullandığınız düzenleyicide ve varolan kodu şu kodla değiştirin:

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

Değiştirin `<name>` adınızla. Kaydet **Program.cs**. Tür `dotnet run` konsol pencerenizde denemek için.

Yalnızca bir dize listesi oluşturduğunuz, üç adları bu listeye eklenmesine ve tamamı büyük harf adları kullanıma yazdırılır. Önceki öğreticilerde listede döngü öğrendiniz kavramları kullanıyorsunuz.

Görünen adları için kodu kullanır [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliği.  Ne zaman önünde bir `string` ile `$` karakter dizesi bildiriminde C# kod ekleme. Gerçek dize, C# kodu ürettiği değeri ile değiştirir. Bu örnekte, onu değiştirir `{name.ToUpper()}` her addaki aradığınız çünkü harfleri büyük olacak şekilde dönüştürülmüş <xref:System.String.ToUpper%2A> yöntemi.

Şimdi keşfetmeye devam etmek.

## <a name="modify-list-contents"></a>Liste içeriklerini değiştirme

Kullanan oluşturduğunuz koleksiyonda <xref:System.Collections.Generic.List%601> türü. Bu tür, öğelerin sıralarının depolar. Açılı ayraçlar arasındaki öğelerin türünü belirtin.

Bu önemli bir özelliği <xref:System.Collections.Generic.List%601> türüdür bunu büyüyebilen veya küçülebilen, ekleme veya öğeleri kaldırma olanak sağlar. Kapatmadan önce bu kodu ekleyin `}` içinde `Main` yöntemi:

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

Listenin sonuna iki daha fazla ad ekledik. Ayrıca bir de kaldırdınız. Dosya ve tür kaydetme `dotnet run` denemek için.

<xref:System.Collections.Generic.List%601> Tek tek öğeler tarafından başvuruda sayesinde **dizin** de. Arasında dizine yerleştirdiğiniz `[` ve `]` liste adı aşağıdaki belirteçleri. C#0 için ilk dizinini kullanır. Yeni eklediğiniz kodun hemen altına bu kodu ekleyin ve deneyin:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Bir dizin listesi ötesinde erişemez. En büyük geçerli dizin olduğundan dizinleri 0'da başlar unutmayın listedeki öğelerin sayısından küçük. Listenin ne kadar süre kullandığı denetleyebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> özelliği. Main yönteminin sonunda aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Dosya ve tür kaydetme `dotnet run` yeniden sonuçları görmek için.

## <a name="search-and-sort-lists"></a>Arama ve sıralama listeler

Örneklerimizi görece küçük listeleri kullanın, ancak uygulamalarınızın genellikle bazen bin numaralandırma çok daha fazla öğe ile listeleri oluşturabilirsiniz. İçinde büyük bu koleksiyonlara öğeleri bulmak için farklı öğeler listesinde arama yapmanız gerekmiyor. <xref:System.Collections.Generic.List%601.IndexOf%2A> Yöntemi bir öğe için arar ve öğenin indisini döndürür. Bu kodu altına ekleyin, `Main` yöntemi:

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

Listenizdeki öğeleri de sıralanabilir. <xref:System.Collections.Generic.List%601.Sort%2A> Yöntemi (alfabetik sırada durumunda dizeler) normal sıralarına listesinden tüm öğeleri sıralar. Bu kod bölmenizin altına eklemek bizim `Main` yöntemi:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Dosya ve tür Kaydet `dotnet run` en son sürümü denemek için.

Sonraki bölümde başlamadan önce geçerli kodu ayrı bir yöntem geçelim. Bu, yeni bir örnek ile çalışmaya başlamak kolaylaştırır. Yeniden adlandırma, `Main` yönteme `WorkingWithStrings` ve yeni bir yazma `Main` metoduna çağrı yapan `WorkingWithStrings`. İşiniz bittiğinde, kodunuzun şu şekilde görünmelidir:

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
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

Kullanmakta olduğunuz `string` şimdiye listelerindeki türü. Olalım bir <xref:System.Collections.Generic.List%601> kullanarak farklı bir tür. Bir dizi sayının oluşturalım.

Aşağıdaki yeni altına ekleyin `Main` yöntemi:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Tamsayı listesi oluşturur ve ilk iki tamsayı 1 değerine ayarlar. İlk iki değerlerini bunlar bir *Fibonacci dizisi*, bir sayı dizisi üzerinde. Önceki iki sayının toplamı gerçekleştirerek sonraki her Fibonacci numarası bulunamadı. Bu kodu ekleyin:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Dosya ve tür Kaydet `dotnet run` sonuçları görmek için.

> [!TIP]
> Bu bölümde üzerinde yoğunlaşmak için çağıran kodu yorum yapabilecek `WorkingWithStrings();`. Yalnızca iki yerleştirme `/` bu gibi karakterler çağrısının önünde: `// WorkingWithStrings();`.

## <a name="challenge"></a>Sınama

Birlikte koyabilirsiniz varsa bkz. bazı kavramlar ve daha önce bu dersler. Ne kadar Fibonacci numaralarıyla derlediğiniz genişletin. Dizideki ilk 20 sayılar üretmek için kod yazmak bu seçeneği deneyin. (Bir ipucu olarak 20 Fibonacci 6765 numarasıdır.)

## <a name="complete-challenge"></a>Görevi tamamlama

Örnek bir çözüm tarafından gördüğünüz [tamamlanan örnek koda Github'da bakmak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)

Döngünün her yinelemesinden son iki tamsayının listesinde, bunları fiyatının ve bu değer, listeye eklemeyi yönlendiriyoruz. 20 öğe listesine ekleyene kadar döngü tekrarlanır.

Tebrikler, liste öğreticisini tamamladınız. İle devam edebilir [sınıflara giriş](introduction-to-classes.md) kendi geliştirme ortamınızda öğretici.

İle çalışma hakkında daha fazla bilgi `List` yazın [.NET Kılavuzu](../../../standard/index.md) konuda [koleksiyonları](../../../standard/collections/index.md). Ayrıca diğer birçok koleksiyon türleri hakkında bilgi edineceksiniz.