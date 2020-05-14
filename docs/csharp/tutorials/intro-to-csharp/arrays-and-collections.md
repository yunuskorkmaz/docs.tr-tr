---
title: Koleksiyonlarla çalışma-C# öğreticisine giriş
description: Bu öğreticide liste koleksiyonunu inceleyerek C# öğrenin.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: c99f5582702120db238de1206de42d964837cdbd
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396890"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a>Genel liste türünü kullanarak veri koleksiyonlarını yönetmeyi öğrenin

Bu giriş öğreticisi, C# diline ve sınıfının temel bilgilerine bir giriş sağlar <xref:System.Collections.Generic.List%601> .

Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir. [10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir. Kullanacağınız komutlara hızlı bir genel bakış, daha fazla ayrıntı bağlantılarıyla birlikte [geliştirme araçları hakkında bilgi sahibi](local-environment.md)olmak için kullanılır.

## <a name="a-basic-list-example"></a>Temel liste örneği

*List-öğreticisi*adlı bir dizin oluşturun. Geçerli dizini oluşturun ve çalıştırın `dotnet new console` .

En sevdiğiniz düzenleyicide *program.cs* açın ve mevcut kodu aşağıdaki kodla değiştirin:

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

`<name>`Adınızla değiştirin. *Program.cs* dosyasını kaydedin. `dotnet run`Denemek için konsol pencerenizi yazın.

Dizelerin bir listesini oluşturdunuz, bu listeye üç ad eklediniz ve adları tüm büyük harfler halinde yazdırdık. Önceki öğreticilerde, listede döngü gerçekleştirmek için öğrenmiş olduğunuz kavramları kullanıyorsunuz.

Adları görüntülenecek kod, [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) özelliğini kullanır.  Bir `string` `$` karakterden önce karakterinden sonra, C# kodunu dize bildirimine ekleyebilirsiniz. Gerçek dize, bu C# kodunun oluşturduğu değerle değiştirir. Bu örnekte, yöntemini çağırdığı için, her bir adla ' ı, `{name.ToUpper()}` büyük harflere dönüştürülecek şekilde değiştirir <xref:System.String.ToUpper%2A> .

Araştırma devam edelim.

## <a name="modify-list-contents"></a>Liste içeriğini değiştirme

Oluşturduğunuz koleksiyon <xref:System.Collections.Generic.List%601> türünü kullanır. Bu tür öğe dizilerini depolar. Açılı ayraçlar arasındaki öğelerin türünü belirtirsiniz.

Bu türün önemli bir yönü <xref:System.Collections.Generic.List%601> büyümenin veya küçülebileceği, öğe eklemenize veya kaldırmanıza imkan sağlar. Yöntemdeki kapatmadan önce bu kodu ekleyin `}` `Main` :

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

Liste sonunun ötesinde bir dizine erişemezsiniz. Dizinlerin 0 ' dan başlayıp, en büyük geçerli dizinin listedeki öğe sayısından bir daha az olması gerektiğini unutmayın. Listenin özelliğini ne kadar süreyle kullandığını kontrol edebilirsiniz <xref:System.Collections.Generic.List%601.Count%2A> . Main yönteminin sonuna aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

Dosyayı kaydedin ve `dotnet run` sonuçları görmek için yeniden yazın.

## <a name="search-and-sort-lists"></a>Arama ve sıralama listeleri

Örneklerimizde görece küçük listeler kullanılıyor, ancak uygulamalarınız genellikle binlerce numaralandırma olan çok sayıda öğesi olan listeler oluşturabilir. Bu daha büyük koleksiyonlardaki öğeleri bulmak için listede farklı öğeler için arama yapmanız gerekir. <xref:System.Collections.Generic.List%601.IndexOf%2A>Yöntemi bir öğe arar ve öğenin dizinini döndürür. Öğe listede yoksa, `IndexOf` döndürür `-1` . Bu kodu yönteminizin en altına ekleyin `Main` :

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

Listenizdeki öğeler de sıralanmış olabilir. <xref:System.Collections.Generic.List%601.Sort%2A>Yöntemi, listedeki tüm öğeleri normal sıralarına göre sıralar (dizeler için alfabetik olarak). Bu kodu yönteminizin en altına ekleyin `Main` :

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

`dotnet run`Bu en son sürümü denemek için dosyayı kaydedin ve yazın.

Sonraki bölüme başlamadan önce geçerli kodu ayrı bir yönteme taşıyalim. Bu, yeni bir örnekle çalışmaya başlamasını kolaylaştırır. `Main`Yönteminizi olarak yeniden adlandırın `WorkingWithStrings` ve çağıran yeni bir `Main` Yöntem yazın `WorkingWithStrings` . İşiniz bittiğinde kodunuzun şöyle görünmesi gerekir:

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

## <a name="lists-of-other-types"></a>Diğer türlerin listeleri

`string`Şu ana kadar listelerdeki türü kullanıyorsunuz. <xref:System.Collections.Generic.List%601>Farklı bir tür kullanalım. Bir sayı kümesi oluşturalım.

Aşağıdakileri yeni yönteminizin altına ekleyin `Main` :

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

Bu, tamsayıların bir listesini oluşturur ve ilk iki tamsayının değerini 1 değerine ayarlar. Bunlar bir *Fibonaccı sırasının*ilk iki değeri, bir dizi sayı. Her bir sonraki Fibonaccı numarası, önceki iki sayının toplamı alınarak bulunur. Şu kodu ekleyin:

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

[GitHub 'daki tamamlanmış örnek koda bakarak](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)örnek bir çözüm görebilirsiniz.

Döngünün her tekrarında, listedeki son iki tamsayının yerine getiriyorsunuz ve bu değeri listeye ekliyor olursunuz. Döngü, listeye 20 öğe ekleyinceye kadar yinelenir.

Tebrikler, liste öğreticisini tamamladınız. Kendi geliştirme ortamınızda [sınıflarla tanışın](introduction-to-classes.md) öğreticisine devam edebilirsiniz.

`List` [Koleksiyonlar](../../../standard/collections/index.md)hakkında [.net Kılavuzu](../../../standard/index.yml) makalesindeki türle çalışma hakkında daha fazla bilgi edinebilirsiniz. Diğer birçok koleksiyon türünü de öğreneceksiniz.
