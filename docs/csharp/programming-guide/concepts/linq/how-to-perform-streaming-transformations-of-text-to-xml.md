---
title: "Nasıl yapılır: XML 'e (C#) metin akışı dönüşümleri gerçekleştirme"
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 6dc48a7342bbeedb79e8e7f4a9270899be336f91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851029"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="7bddd-102">Nasıl yapılır: XML 'e (C#) metin akışı dönüşümleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="7bddd-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>

<span data-ttu-id="7bddd-103">Bir metin dosyasını işlemeye yönelik bir yaklaşım, `yield return` yapıyı kullanarak metin dosyasını bir kerede bir satır akışı yapan bir genişletme yöntemi yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="7bddd-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="7bddd-104">Daha sonra, metin dosyasını yavaş ertelenmiş bir biçimde işleyen bir LINQ sorgusu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bddd-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="7bddd-105">Daha sonra çıktıyı akışa <xref:System.Xml.Linq.XStreamingElement> almak için öğesini kullanırsanız, kaynak metin dosyasının boyutundan bağımsız olarak en az miktarda bellek kullanan metin dosyasından XML 'e bir dönüşüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bddd-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="7bddd-106">Akış dönüşümleriyle ilgili bazı uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="7bddd-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="7bddd-107">Bir akış dönüştürmesi en iyi şekilde, dosyanın tamamını bir kez işleyebileceğiniz ve satırları kaynak belgede gerçekleştikleri sırada işleyebileceğiniz durumlarda en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7bddd-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="7bddd-108">Dosyayı birden çok kez işlemek istiyorsanız veya satırları işleyebilmeniz için öncelikle sıralama yapmanız gerekiyorsa, bir akış tekniği kullanmanın avantajlarından çoğunu kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="7bddd-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="7bddd-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bddd-109">Example</span></span>

 <span data-ttu-id="7bddd-110">Aşağıdaki metin dosyası, kişiler. txt, bu örneğin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="7bddd-110">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="7bddd-111">Aşağıdaki kod, metin dosyasının satırlarını ertelenmiş bir biçimde akıp bir genişletme yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="7bddd-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

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

 <span data-ttu-id="7bddd-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7bddd-112">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7bddd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bddd-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
