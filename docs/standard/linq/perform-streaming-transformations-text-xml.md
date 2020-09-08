---
title: C#-LINQ to XML metin olarak XML 'e akış dönüştürmeleri gerçekleştirme
description: İşlem için bir metin dosyasını akışa almak üzere bir kerede bir satırı serbest bırakma uzantısı yöntemini kullanabilirsiniz. Bu teknik, tüm dosyayı yükleyen ve sonra işleyen tekniklere kıyasla bellek gereksinimlerini azaltır.
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 8e0d710d7cbc6de8cc60721c211376a82b6c29fc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553919"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a>C# ' de metnin XML 'e akış dönüştürmeleri gerçekleştirme (LINQ to XML)

İşlem için bir metin dosyasını akışa almak üzere bir kerede bir satırı serbest bırakma uzantısı yöntemini kullanabilirsiniz. Bu teknik, tüm dosyayı yükleyen ve sonra işleyen tekniklere kıyasla bellek gereksinimlerini azaltır.

Genişletme yöntemi, yapıyı kullanarak satırı sağlayabilir `yield return` . Bir LINQ sorgusu, akışı yavaş ertelenmiş bir biçimde işleyebilir. <xref:System.Xml.Linq.XStreamingElement>Çıktıyı akışa almak için kullanırsanız, kaynak metin dosyasının boyutundan bağımsız olarak en az miktarda belleği kullanan metin DOSYASıNDAN XML 'e bir dönüşüm oluşturabilirsiniz.

> [!NOTE]
> Bu teknik en iyi şekilde, tüm dosyayı bir kez işleyebilmeniz ve satırları kaynak belgeden sırayla ele almanız durumunda en iyi şekilde uygulanır. Dosyayı birden çok kez işleme veya işlemeden önce sıralama, bir akış tekniğinin performans avantajlarını azaltır.

## <a name="example-use-an-extension-method-to-stream-text"></a>Örnek, metin akışı için bir genişletme yöntemi kullanın

Örnek, People.txt, kaynağı olarak aşağıdaki metin dosyasını kullanır:

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

Örneğin kodunda, genişletme yöntemi `Lines` metni bir kerede bir satır sağlar:

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

Örnek aşağıdaki çıktıyı üretir:

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
