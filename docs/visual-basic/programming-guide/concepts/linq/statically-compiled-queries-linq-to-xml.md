---
title: Sorgular (LINQ to XML)'statik olarak derlenmiş (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: ff708dd14d27b34be797f1630dabe27a56c5a219
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834913"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Sorgular (LINQ to XML)'statik olarak derlenmiş (Visual Basic)
En önemli performans birini avantajlar LINQ, XML olarak <xref:System.Xml.XmlDocument>, XPath sorguları çalışma zamanında yorumlanacağını ancak LINQ to XML sorgularında statik olduğunu, derlenir. Bu özellik için LINQ to XML, yararlanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknolojiyi arasında seçim yaparken, aradaki farkı kavramak yararlıdır yerleşik olarak bulunur. Bu konu, farkı açıklar.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenmiş sorgular vs. XPath  
 Aşağıdaki örnek belirtilen ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğeleri almak nasıl gösterir.  
  
 Eşdeğer XPath ifadesi verilmiştir:  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnekte sorgu ifadesi metot tabanlı sorgu söz dizimi için derleyici tarafından yeniden yazılır. Metot tabanlı sorgu söz dizimi içinde yazılır, aşağıdaki örnekte, önceki'dekiyle aynı sonucu üretir:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Bir genişletme yöntemi bir yöntemdir. Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Çünkü <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemi, yukarıdaki sorgunun yazılmış gibi sorgulamanıza şu şekilde derlenir:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu sorgular, statik olarak bağlı yöntemi çağrılarını etkili bir şekilde derlenir olgu gösterilmektedir. Bu, yineleyiciler, ertelenmiş yürütme semantikleri ile birleştirilmiş performansını artırır. Yineleyiciler ertelenmiş yürütme semantikleri hakkında daha fazla bilgi için bkz. [ertelenmiş yürütme ve geç değerlendirme LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Bu örnekler derleyici yazabilirsiniz kodun temsilcisi. Gerçek uygulamalar bu örneklerden biraz farklı olabilir, ancak performans aynı olacaktır ya da bu örneklerde benzer.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XPath ifadeleri XmlDocument ile çalıştırma  
 Aşağıdaki örnekte <xref:System.Xml.XmlDocument> önceki örnekler aynı sonuçlara ulaşmak için:  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 Bu sorgu, LINQ to XML kullanan örnekler aynı çıkışı döndürür; tek fark LINQ to XML yazdırılan XML girintiler takvimidir <xref:System.Xml.XmlDocument> desteklemez.  
  
 Ancak, <xref:System.Xml.XmlDocument> yaklaşımı genellikle gerçekleştirmez LINQ to XML, yanı sıra çünkü <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi aşağıdakileri yapmalıdır dahili olarak her çağrıldığında:  
  
-   Bu dizeyi belirteçlere bozucu bir XPath ifadesi içeriyor dizeyi ayrıştırır.  
  
-   Bu XPath ifadesi geçerli olduğundan emin olmak için belirteçlerini doğrular.  
  
-   Bu iç ifade ağacı ifadeye çevrilir.  
  
-   Uygun şekilde ifade değerlendirmeye göre sonuç kümesi için düğümleri seçme düğümleri aracılığıyla yinelenir.  
  
 Önemli ölçüde daha fazla ilgili LINQ to XML sorgusu ile çalışmanın budur. Sorgu farklı türleri için belirli bir performans farkı değişir, ancak genel bir LINQ to XML sorguları daha az çalışma yapın ve bu nedenle, daha iyi kullanarak XPath ifadelerini değerlendirme gerçekleştirmek <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
