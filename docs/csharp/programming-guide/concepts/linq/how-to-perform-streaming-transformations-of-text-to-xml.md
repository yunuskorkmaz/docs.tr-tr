---
title: "Nasıl yapılır: Metinden XML'e akış dönüşümleri gerçekleştirme (C#)"
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 906150483f7f76b4429ea390d083e9f18696ac9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667879"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="1c66f-102">Nasıl yapılır: Metinden XML'e akış dönüşümleri gerçekleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="1c66f-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="1c66f-103">Bir metin dosyasını işlerken bir yaklaşım kullanarak bir defada bir satır metin dosyası akışı uzantı metodu yazma etmektir `yield return` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c66f-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="1c66f-104">Ardından, yavaş ertelenmiş biçimde metin dosyası işleyen bir LINQ sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c66f-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="1c66f-105">Ardından kullanırsanız <xref:System.Xml.Linq.XStreamingElement> akış çıkışı için daha sonra bir dönüştürme metin dosyasından en az bir kaynak metin dosyasının boyutu ne olursa olsun, bellek miktarını kullanır XML oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c66f-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="1c66f-106">Akış dönüşümleri ile ilgili bazı uyarılar vardır.</span><span class="sxs-lookup"><span data-stu-id="1c66f-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="1c66f-107">Akış bir dönüşüm, burada sonra ve kaynak belgesinde gerçekleştikleri sırada satırları işleyebilirsiniz dosyanın tamamı işleyebilir durumlarda en iyi şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1c66f-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="1c66f-108">Birden çok kez dosyayı işlemek zorunda ya da bunları işleyebilmesi satırları sıralamak varsa, bir akış teknik kullanmanın avantajları birçoğu kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="1c66f-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c66f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c66f-109">Example</span></span>  
 <span data-ttu-id="1c66f-110">Aşağıdaki metin dosyası People.txt, bu örnekte kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="1c66f-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="1c66f-111">Aşağıdaki kod, ertelenmiş bir biçimde metin dosyası satırlarını akışları bir genişletme yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="1c66f-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
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
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
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
  
 <span data-ttu-id="1c66f-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1c66f-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c66f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c66f-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
- [<span data-ttu-id="1c66f-114">Gelişmiş sorgu teknikleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1c66f-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
