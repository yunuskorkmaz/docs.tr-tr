---
title: Metnin XML 'e akış dönüştürmeleri gerçekleştirme (C#)
description: Metin dosyasını tek seferde bir satır olarak akıtmak ve metin dosyasını işlemek için bir LINQ sorgusu kullanmak üzere C# ' de metin olarak XML 'e akış dönüşümü yapmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104752"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Metnin XML 'e akış dönüştürmeleri gerçekleştirme (C#)

Bir metin dosyasını işlemeye yönelik bir yaklaşım, yapıyı kullanarak metin dosyasını bir kerede bir satır akışı yapan bir genişletme yöntemi yazmaktır `yield return` . Daha sonra, metin dosyasını yavaş ertelenmiş bir biçimde işleyen bir LINQ sorgusu yazabilirsiniz. Daha sonra <xref:System.Xml.Linq.XStreamingElement> çıktıyı akışa almak için öğesini kullanırsanız, kaynak metin dosyasının boyutundan bağımsız olarak en az miktarda bellek kullanan metin DOSYASıNDAN XML 'e bir dönüşüm oluşturabilirsiniz.

 Akış dönüşümleriyle ilgili bazı uyarılar vardır. Bir akış dönüştürmesi en iyi şekilde, dosyanın tamamını bir kez işleyebileceğiniz ve satırları kaynak belgede gerçekleştikleri sırada işleyebileceğiniz durumlarda en iyi şekilde uygulanır. Dosyayı birden çok kez işlemek istiyorsanız veya satırları işleyebilmeniz için öncelikle sıralama yapmanız gerekiyorsa, bir akış tekniği kullanmanın avantajlarından çoğunu kaybedersiniz.

## <a name="example"></a>Örnek

 Aşağıdaki metin dosyası People.txt, bu örneğin kaynağıdır.

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 Aşağıdaki kod, metin dosyasının satırlarını ertelenmiş bir biçimde akıp bir genişletme yöntemi içerir.

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

 Bu örnek aşağıdaki çıktıyı üretir:

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
