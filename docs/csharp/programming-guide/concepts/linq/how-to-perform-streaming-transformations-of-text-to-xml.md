---
title: 'Nasıl yapılır: XML (C#) için metin akış dönüştürmeleri gerçekleştirebilirsiniz'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 4313c5263b6a219ec3c8d05a7b7938c41c7cc028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328194"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="c6789-102">Nasıl yapılır: XML (C#) için metin akış dönüştürmeleri gerçekleştirebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="c6789-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="c6789-103">Bir metin dosyası işleme için bir yaklaşım ise metin dosyası akışları bir genişletme yöntemi kullanarak bir defada bir satır yazmak için `yield return` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6789-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="c6789-104">Ardından, yavaş bir ertelenmiş şekilde metin dosyasında işler bir LINQ sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6789-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="c6789-105">Ardından kullanırsanız <xref:System.Xml.Linq.XStreamingElement> akış çıkışı için daha sonra bir dönüşüm metin dosyasından en az bir kaynak metin dosyasının boyutunu bağımsız olarak bellek miktarını kullanır XML oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6789-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="c6789-106">Akış dönüşümleri ilgili bazı uyarılar var.</span><span class="sxs-lookup"><span data-stu-id="c6789-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="c6789-107">Bir akış dönüştürmesi en iyi yeri sonra ve kaynak belgesinde oluşma sırada satırları işlem, dosyanın tamamı işleyebilir durumlarda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c6789-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="c6789-108">Dosyanın birden çok kez işlemek varsa veya bunları işlemeden önce satırları sıralamak varsa, bir akış teknik kullanmanın avantajları çoğunu kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="c6789-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6789-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6789-109">Example</span></span>  
 <span data-ttu-id="c6789-110">Aşağıdaki metin dosyası People.txt, bu örnek kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="c6789-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="c6789-111">Aşağıdaki kod satırları ertelenmiş biçimde metin dosyasının akışları bir genişletme yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="c6789-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
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
  
 <span data-ttu-id="c6789-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c6789-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6789-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6789-113">See Also</span></span>  
 <xref:System.Xml.Linq.XStreamingElement>  
 [<span data-ttu-id="c6789-114">Gelişmiş sorgu teknikler (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c6789-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
