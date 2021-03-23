---
title: Koleksiyonlarla çalışma-C# öğreticisine giriş
description: Bu öğreticide liste koleksiyonunu inceleyerek C# öğrenin.
ms.date: 02/05/2021
ms.openlocfilehash: 0043372aed65fbc720a022a3d8c69abd25ceca0c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876109"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin

Bu giriş öğreticisi, C# diline ve sınıfının temel bilgilerine bir giriş sağlar <xref:System.Collections.Generic.List%601> .

## <a name="prerequisites"></a>Önkoşullar

Öğretici, yerel geliştirme için ayarlanmış bir makineniz olmasını bekler. Windows, Linux veya macOS 'ta, uygulamaları oluşturmak, derlemek ve çalıştırmak için .NET CLı kullanabilirsiniz. Mac ve Windows 'da, Visual Studio 2019 ' i kullanabilirsiniz. Kurulum yönergeleri için bkz. [Yerel ortamınızı ayarlama](local-environment.md).

## <a name="a-basic-list-example"></a>Temel liste örneği

*List-öğreticisi* adlı bir dizin oluşturun. Geçerli dizini oluşturun ve çalıştırın `dotnet new console` .

*Program. cs* ' yi en sevdiğiniz düzenleyicide açın ve mevcut kodu aşağıdaki kodla değiştirin:

```csharp
using System;
using System.Collections.Generic;

var names = new List<string> { "<name>", "Ana", "Felipe" };
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

`<name>`Adınızla değiştirin. *Program.cs* dosyasını kaydedin. `dotnet run`Denemek için konsol pencerenizi yazın.

Dizelerin bir listesini oluşturdunuz, bu listeye üç ad eklediniz ve adları tüm büyük harfler halinde yazdırdık. Önceki öğreticilerde, listede döngü gerçekleştirmek için öğrenmiş olduğunuz kavramları kullanıyorsunuz.

Adları görüntülenecek kod, [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliğini kullanır.  Bir `string` `$` karakterden önce karakterinden sonra, C# kodunu dize bildirimine ekleyebilirsiniz. Gerçek dize, bu C# kodunun oluşturduğu değerle değiştirir. Bu örnekte, yöntemini çağırdığı için, her bir adla ' ı, `{name.ToUpper()}` büyük harflere dönüştürülecek şekilde değiştirir <xref:System.String.ToUpper%2A> .

Araştırma devam edelim.

## <a name="modify-list-contents"></a>Liste içeriğini değiştirme

Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır. Bu tür öğe dizilerini depolar. Açılı ayraçlar arasındaki öğelerin türünü belirtirsiniz.

Bu türün önemli bir yönü <xref:System.Collections.Generic.List%601> büyümenin veya küçülebileceği, öğe eklemenize veya kaldırmanıza imkan sağlar. Programınızın sonuna bu kodu ekleyin:

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

Listenin sonuna iki ad daha eklediniz. Ayrıca bir tane de kaldırmış olursunuz. Dosyayı kaydedin ve `dotnet run` denemek için yazın.

, <xref:System.Collections.Generic.List%601> Tek tek öğeleri **dizine** göre de başvurmanızı sağlar. Dizini, `[` `]` liste adını izleyen ve belirteçleri arasına yerleştirebilirsiniz. C# ilk dizin için 0 kullanır. Bu kodu, yeni eklediğiniz kodun hemen altına ekleyin ve deneyin:

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

Liste sonunun ötesinde bir dizine erişemezsiniz. Dizinlerin 0 ' dan başlayıp, en büyük geçerli dizinin listedeki öğe sayısından bir daha az olması gerektiğini unutmayın. Listenin özelliğini ne kadar süreyle kullandığını kontrol edebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> . Programınızın sonuna aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Dosyayı kaydedin ve `dotnet run` sonuçları görmek için yeniden yazın.

## <a name="search-and-sort-lists"></a>Arama ve sıralama listeleri

Örneklerimizde görece küçük listeler kullanılıyor, ancak uygulamalarınız genellikle binlerce numaralandırma olan çok sayıda öğesi olan listeler oluşturabilir. Bu daha büyük koleksiyonlardaki öğeleri bulmak için listede farklı öğeler için arama yapmanız gerekir. <xref:System.Collections.Generic.List%601.IndexOf%2A>Yöntemi bir öğe arar ve öğenin dizinini döndürür. Öğe listede yoksa, `IndexOf` döndürür `-1` . Bu kodu programınızın altına ekleyin:

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

Listenizdeki öğeler de sıralanmış olabilir. <xref:System.Collections.Generic.List%601.Sort%2A>Yöntemi, listedeki tüm öğeleri normal sıralarına göre sıralar (dizeler için alfabetik olarak). Bu kodu programınızın altına ekleyin:

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

`dotnet run`Bu en son sürümü denemek için dosyayı kaydedin ve yazın.

Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. Yazdığınız tüm kodu adlı yeni bir yöntemde yerleştirin `WorkWithStrings()` . Programınızın en üstünde bu yöntemi çağırın. Bitirdiğinizde, kodunuzun şöyle görünmesi gerekir:

```csharp
using System;
using System.Collections.Generic;

WorkWithString();

void WorkWithString()
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
```

## <a name="lists-of-other-types"></a>Diğer türlerin listeleri

`string`Şu ana kadar listelerdeki türü kullanıyorsunuz. <xref:System.Collections.Generic.List%601>Farklı bir tür kullanalım. Bir sayı kümesi oluşturalım.

' İ çağırdıktan sonra programınıza aşağıdakileri ekleyin `WorkWithStrings()` :

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Bu, tamsayıların bir listesini oluşturur ve ilk iki tamsayının değerini 1 değerine ayarlar. Bunlar bir *Fibonaccı sırasının* ilk iki değeri, bir dizi sayı. Her bir sonraki Fibonaccı numarası, önceki iki sayının toplamı alınarak bulunur. Şu kodu ekleyin:

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

Sonuçları görmek için dosyayı kaydedin ve yazın `dotnet run` .

> [!TIP]
> Yalnızca bu bölüme odaklanmak için, çağıran kodu açıklama olarak ayarlayabilirsiniz `WorkingWithStrings();` . `/`Çağrının önüne şu şekilde iki karakter koymanız yeterlidir: `// WorkingWithStrings();` .

## <a name="challenge"></a>Sınama

Bu ve önceki derslerden bazılarını bir araya getirebilirsiniz. Fibonaccı numaralarına en fazla ne kadar derlediğiniz hakkında ' yı genişletin. Dizideki ilk 20 sayıyı oluşturmak için kodu yazmayı deneyin. (İpucu olarak, 20 fibonaccı numarası 6765 ' dir.)

## <a name="complete-challenge"></a>Görevi tamamlama

[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/main/csharp/list-quickstart/Program.cs#L8-L16)örnek bir çözüm görebilirsiniz.

Döngünün her tekrarında, listedeki son iki tamsayının yerine getiriyorsunuz ve bu değeri listeye ekliyor olursunuz. Döngü, listeye 20 öğe ekleyinceye kadar yinelenir.

Tebrikler, liste öğreticisini tamamladınız. Kendi geliştirme ortamınızda [ek](../../tutorials/index.md) öğreticilerle devam edebilirsiniz.

`List` [Koleksiyonlar](../../../standard/collections/index.md)üzerinde .net temelleri makalesindeki türle çalışma hakkında daha fazla bilgi edinebilirsiniz. Diğer birçok koleksiyon türünü de öğreneceksiniz.
