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
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="5f481-103">Metnin XML 'e akış dönüştürmeleri gerçekleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="5f481-103">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="5f481-104">Bir metin dosyasını işlemeye yönelik bir yaklaşım, yapıyı kullanarak metin dosyasını bir kerede bir satır akışı yapan bir genişletme yöntemi yazmaktır `yield return` .</span><span class="sxs-lookup"><span data-stu-id="5f481-104">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="5f481-105">Daha sonra, metin dosyasını yavaş ertelenmiş bir biçimde işleyen bir LINQ sorgusu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f481-105">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="5f481-106">Daha sonra <xref:System.Xml.Linq.XStreamingElement> çıktıyı akışa almak için öğesini kullanırsanız, kaynak metin dosyasının boyutundan bağımsız olarak en az miktarda bellek kullanan metin DOSYASıNDAN XML 'e bir dönüşüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f481-106">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="5f481-107">Akış dönüşümleriyle ilgili bazı uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="5f481-107">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="5f481-108">Bir akış dönüştürmesi en iyi şekilde, dosyanın tamamını bir kez işleyebileceğiniz ve satırları kaynak belgede gerçekleştikleri sırada işleyebileceğiniz durumlarda en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5f481-108">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="5f481-109">Dosyayı birden çok kez işlemek istiyorsanız veya satırları işleyebilmeniz için öncelikle sıralama yapmanız gerekiyorsa, bir akış tekniği kullanmanın avantajlarından çoğunu kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="5f481-109">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="5f481-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f481-110">Example</span></span>

 <span data-ttu-id="5f481-111">Aşağıdaki metin dosyası People.txt, bu örneğin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="5f481-111">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="5f481-112">Aşağıdaki kod, metin dosyasının satırlarını ertelenmiş bir biçimde akıp bir genişletme yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="5f481-112">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

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

 <span data-ttu-id="5f481-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5f481-113">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5f481-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f481-114">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
