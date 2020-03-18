---
title: Koleksiyonlarla çalışma - C# eğitimine giriş
description: Bu öğreticide Liste koleksiyonunu inceleyerek C# öğrenin.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 25d20de2eae8ad1f544fa17553c173a6141ae464
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156695"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin

Bu giriş öğretici c# dili ve <xref:System.Collections.Generic.List%601> sınıfın temelleri için bir giriş sağlar.

Bu öğretici, geliştirme için kullanabileceğiniz bir makineye sahip olmak için bekliyor. .NET öğretici [Hello World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) Windows, Linux veya macOS'ta yerel geliştirme ortamınızı ayarlama talimatları na sahiptir. Kullanacağınız komutların hızlı bir genel bakışı, daha fazla ayrıntıya bağlantılar içeren [geliştirme araçlarına aşina olun'da](local-environment.md)dır.

## <a name="a-basic-list-example"></a>Temel bir liste örneği

*Liste öğretici*adlı bir dizin oluşturun. Geçerli dizini ve çalıştır `dotnet new console`ın.

Sık kullanılan düzenleyicide *Program.cs* açın ve varolan kodu aşağıdakilerle değiştirin:

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

Adınız ile değiştirin. `<name>` *Program.cs* dosyasını kaydedin. Denemek `dotnet run` için konsol pencerenizi yazın.

Dizeleri bir liste oluşturdunuz, bu listeye üç ad eklediniz ve tüm CAPS'lerde adları yazdırdın. Listeyi gözden geçirmek için önceki öğreticilerde öğrendiğiniz kavramları kullanıyorsunuz.

Adları görüntülemek için kod [dize enterpolasyon](../../language-reference/tokens/interpolated.md) özelliğini kullanır.  `$` Karakterle bir `string` önce olduğunuzda, dize bildirimine C# kodunu katıştırabilirsiniz. Gerçek dize, c# kodunu oluşturduğu değerle değiştirir. Bu örnekte, `{name.ToUpper()}` <xref:System.String.ToUpper%2A> yöntemi çağırdığınız için büyük harfe dönüştürülen her adla değiştirilir.

Keşfetmeye devam edelim.

## <a name="modify-list-contents"></a>Liste içeriğini değiştirme

Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır. Bu tür öğelerin dizileri depolar. Açı braketleri arasındaki öğelerin türünü belirtirsiniz.

Bu <xref:System.Collections.Generic.List%601> türün önemli bir yönü, öğeleri eklemenize veya kaldırmanıza olanak sağlayarak büyüyebilir veya küçülebilir. `Main` Yöntemde kapanışönce `}` bu kodu ekleyin:

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

Listenin sonuna iki ad daha eklediniz. Bir tanesini de kaldırdın. Dosyayı kaydedin `dotnet run` ve denemek için yazın.

<xref:System.Collections.Generic.List%601> Dizin bazında tek tek **index** öğelere başvurmanızı sağlar. Dizini liste `[` adını `]` izleyen belirteçler arasına yerebilirsiniz. C# ilk dizin için 0 kullanır. Bu kodu eklediğiniz kodun hemen altına ekleyin ve deneyin:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Listenin sonundan sonra bir dizin erişemezsiniz. Endekslerin 0'dan başladığını unutmayın, bu nedenle en büyük geçerli dizin listedeki öğe sayısından bir azdır. Listenin <xref:System.Collections.Generic.List%601.Count%2A> özelliği ne kadar süreyle kullandığını kontrol edebilirsiniz. Ana yöntemin sonuna aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Dosyayı kaydedin `dotnet run` ve sonuçları görmek için yeniden yazın.

## <a name="search-and-sort-lists"></a>Listeleri arama ve sıralama

Örneklerimiz nispeten küçük listeler kullanır, ancak uygulamalarınız genellikle daha fazla öğeiçeren listeler oluşturabilir ve bazen binlercesini numaralandırmak gerekir. Bu büyük koleksiyonlarda öğeleri bulmak için, farklı öğeler için listearama nız gerekir. Yöntem <xref:System.Collections.Generic.List%601.IndexOf%2A> bir öğeyi arar ve öğenin dizinini döndürür. Bu kodu yönteminizin `Main` altına ekleyin:

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

Listenizdeki öğeler de sıralanabilir. Yöntem, <xref:System.Collections.Generic.List%601.Sort%2A> listedeki tüm öğeleri normal sıralarına göre sıralar (dizeleri durumunda alfabetik olarak). Bu kodu yöntemimizin `Main` altına ekleyin:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

Bu son sürümü `dotnet run` denemek için dosyayı kaydedin ve yazın.

Bir sonraki bölümü başlatmadan önce, geçerli kodu ayrı bir yönteme taşıyalım. Bu, yeni bir örnekle çalışmaya başlamayı kolaylaştırır. Metodunuzu `WorkingWithStrings` yeniden adlandırın `Main` `Main` ve `WorkingWithStrings`çağıran yeni bir yöntem yazın. Bitirdikten sonra, kodunuz şu şekilde görünmelidir:

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

        static void WorkingWithStrings()
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
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a>Diğer türler deki listeler

Şu ana kadar `string` listelerdeki türü kullanıyorsunuz. Farklı bir <xref:System.Collections.Generic.List%601> tür kullanarak yapalım. Bir dizi sayı oluşturalım.

Yeni `Main` yönteminizin altına aşağıdakileri ekleyin:

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Bu, tamsayılar listesi oluşturur ve ilk iki tamsayıdeğerini 1 değerine ayarlar. Bunlar *fibonacci dizisinin*ilk iki değeridir, bir sayı dizisi. Sonraki her Fibonacci numarası önceki iki sayının toplamı alınarak bulunur. Şu kodu ekleyin:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Sonuçları görmek için `dotnet run` dosyayı kaydedin ve yazın.

> [!TIP]
> Sadece bu bölüme odaklanmak için, çağıran `WorkingWithStrings();`kodu yorumlayabilirsiniz. Sadece bu `/` gibi arama önünde iki karakter `// WorkingWithStrings();`koyun: .

## <a name="challenge"></a>Sınama

Bu ve daha önceki derslerden bazı kavramları bir araya getirebilecek olup olmadığını görün. Fibonacci Numbers ile şimdiye kadar inşa ettiğiniz şeyi genişletin. Dizideki ilk 20 sayıyı oluşturmak için kodu yazmaya çalışın. (İpucu olarak, 20 Fibonacci sayısı 6765'tir.)

## <a name="complete-challenge"></a>Görevi tamamlama

[GitHub'da bitmiş örnek koduna bakarak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)örnek bir çözüm görebilirsiniz.

Döngünün her yinelemesinde, listedeki son iki sondayı alıp, bunları özetliyor ve bu değeri listeye ekliyorsunuz. Listeye 20 öğe ekleyene kadar döngü yineler.

Tebrikler, liste eğitimini tamamladınız. Kendi geliştirme ortamınızda [sınıflara Giriş](introduction-to-classes.md) eğitimi ile devam edebilirsiniz.

[Koleksiyonlarla](../../../standard/collections/index.md)ilgili [.NET](../../../standard/index.md) `List` Guide konusunun türüyle çalışma hakkında daha fazla bilgi edinebilirsiniz. Ayrıca diğer birçok koleksiyon türü hakkında da bilgi edineceksiniz.
