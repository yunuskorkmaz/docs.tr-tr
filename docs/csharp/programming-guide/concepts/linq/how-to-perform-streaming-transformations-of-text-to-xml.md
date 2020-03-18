---
title: Metnin XML'e akış dönüşümleri (C#) nasıl yapılır?
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345789"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Metnin XML'e akış dönüşümleri (C#) nasıl yapılır?

Metin dosyasını işlemeye yönelik bir yaklaşım, `yield return` yapıyı kullanarak metin dosyasını bir defada bir satır adadan bir uzantı yöntemi yazmaktır. Daha sonra, metin dosyasını tembel bir şekilde işleyen bir LINQ sorgusu yazabilirsiniz. Daha sonra <xref:System.Xml.Linq.XStreamingElement> çıktı akışı için kullanırsanız, kaynak metin dosyasının boyutune bakılmaksızın, metin dosyasından XML'ye, en az miktarda bellek kullanan bir dönüşüm oluşturabilirsiniz.

 Akış dönüşümleri ile ilgili bazı uyarılar vardır. Akış dönüşümü, tüm dosyayı bir kez işleyebilir ve satırları kaynak belgede oluşacak sırayla işleyebilirseniz, en iyi şekilde uygulanır. Dosyayı birden fazla kez işlemeniz gerekiyorsa veya satırları işlemeden önce sıralamanız gerekiyorsa, akış tekniği kullanmanın birçok avantajını kaybedersiniz.

## <a name="example"></a>Örnek

 Aşağıdaki metin dosyası, People.txt, bu örneğin kaynağıdır.

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 Aşağıdaki kod, metin dosyasının satırlarını ertelenmiş bir şekilde aktaran bir uzantı yöntemi içerir.

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 Bu örnek, aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XStreamingElement>
