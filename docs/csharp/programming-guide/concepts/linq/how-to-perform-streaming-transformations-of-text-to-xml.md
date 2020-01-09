---
title: XML 'e (C#) metin akışı dönüşümleri gerçekleştirme
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345789"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>XML 'e (C#) metin akışı dönüşümleri gerçekleştirme

Bir metin dosyasını işlemeye yönelik bir yaklaşım, `yield return` yapısını kullanarak metin dosyasını tek seferde bir satır akışı yapan bir genişletme yöntemi yazmaktır. Daha sonra, metin dosyasını yavaş ertelenmiş bir biçimde işleyen bir LINQ sorgusu yazabilirsiniz. Daha sonra çıktıyı akışa almak için <xref:System.Xml.Linq.XStreamingElement> kullanırsanız, kaynak metin dosyasının boyutundan bağımsız olarak en az miktarda bellek kullanan metin dosyasından XML 'e bir dönüşüm oluşturabilirsiniz.

 Akış dönüşümleriyle ilgili bazı uyarılar vardır. Bir akış dönüştürmesi en iyi şekilde, dosyanın tamamını bir kez işleyebileceğiniz ve satırları kaynak belgede gerçekleştikleri sırada işleyebileceğiniz durumlarda en iyi şekilde uygulanır. Dosyayı birden çok kez işlemek istiyorsanız veya satırları işleyebilmeniz için öncelikle sıralama yapmanız gerekiyorsa, bir akış tekniği kullanmanın avantajlarından çoğunu kaybedersiniz.

## <a name="example"></a>Örnek

 Aşağıdaki metin dosyası, kişiler. txt, bu örneğin kaynağıdır.

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
