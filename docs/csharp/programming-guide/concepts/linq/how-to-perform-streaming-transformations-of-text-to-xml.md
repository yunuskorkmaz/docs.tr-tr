---
title: "Nasıl yapılır: metinden XML'e (C#) akış dönüşümleri gerçekleştirme"
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 98fa8bd9ae393e9c87b67ae3f2874a2c279415af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526953"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Nasıl yapılır: metinden XML'e (C#) akış dönüşümleri gerçekleştirme
Bir metin dosyasını işlerken bir yaklaşım kullanarak bir defada bir satır metin dosyası akışı uzantı metodu yazma etmektir `yield return` oluşturun. Ardından, yavaş ertelenmiş biçimde metin dosyası işleyen bir LINQ sorgu yazabilirsiniz. Ardından kullanırsanız <xref:System.Xml.Linq.XStreamingElement> akış çıkışı için daha sonra bir dönüştürme metin dosyasından en az bir kaynak metin dosyasının boyutu ne olursa olsun, bellek miktarını kullanır XML oluşturabilirsiniz.  
  
 Akış dönüşümleri ile ilgili bazı uyarılar vardır. Akış bir dönüşüm, burada sonra ve kaynak belgesinde gerçekleştikleri sırada satırları işleyebilirsiniz dosyanın tamamı işleyebilir durumlarda en iyi şekilde uygulanır. Birden çok kez dosyayı işlemek zorunda ya da bunları işleyebilmesi satırları sıralamak varsa, bir akış teknik kullanmanın avantajları birçoğu kaybedersiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki metin dosyası People.txt, bu örnekte kaynağıdır.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Aşağıdaki kod, ertelenmiş bir biçimde metin dosyası satırlarını akışları bir genişletme yöntemi içerir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Xml.Linq.XStreamingElement>  
- [Gelişmiş sorgu teknikleri (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
