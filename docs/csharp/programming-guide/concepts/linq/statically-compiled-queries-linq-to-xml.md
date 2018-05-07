---
title: Sorgu (LINQ-XML)'statik olarak derlenmiş (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: b429a5711be942349365019fc71291f78fccc652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Sorgu (LINQ-XML)'statik olarak derlenmiş (C#)
En önemli performans birini avantaj LINQ XML'e tersine <xref:System.Xml.XmlDocument>, çalışma zamanında XPath sorguları yorumlanacağını ancak LINQ-XML sorgularında statik olduğundan, derlenir. Bu özellik LINQ-XML, onu yararlanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknolojiyi arasında seçerken aralarındaki farkı anlamak faydalıdır şekilde de yerleşiktir. Bu konuda fark açıklanmaktadır.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenmiş sorguları vs. XPath  
 Aşağıdaki örnek belirtilen ada sahip ve belirtilen değerli özniteliği içeren alt öğelerini alma gösterilmektedir.  
  
 Eşdeğer XPath ifadesi verilmiştir:  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek sorgu ifadesinde yöntem temelli sorgu söz dizimi derleyicisi tarafından yeniden yazılır. Yöntem temelli sorgu söz dizimi yazılır, aşağıdaki örnek öncekiyle aynı sonuçları üretir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Bir genişletme yöntemi bir yöntemdir. Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Çünkü <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemidir yazılmış gibi sorgulamanıza gibi yukarıdaki sorgu derlenir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek, önceki iki örnek ile tam olarak aynı sonuçları üretir. Bu sorguları statik olarak bağlantılı yöntemi çağrılarını etkili bir şekilde derlenen olgu gösterilmektedir. Bu, birleştirilmiş yineleyiciler, ertelenmiş yürütme semantiği ile performansı artırır. Yineleyiciler ertelenmiş yürütme semantiğini hakkında daha fazla bilgi için bkz: [ertelenmiş yürütme ve LINQ-XML (C#) geç değerlendirme](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Bu örnekler derleyici yazabilir kod temsilcisi. Gerçek uygulamayı bu örneklerinden biraz farklı olabilir, ancak performans aynı olacaktır ya da bu örneklerde benzer.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XPath ifadeleri XmlDocument ile çalıştırma  
 Aşağıdaki örnek kullanır <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları gerçekleştirmek için:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Bu sorgu LINQ-XML kullanma örnekleri aynı çıktıyı döndürür; yalnızca LINQ-XML yazdırılan XML girintileri ancak farktır <xref:System.Xml.XmlDocument> desteklemez.  
  
 Ancak, <xref:System.Xml.XmlDocument> yaklaşım genellikle gerçekleştirmez LINQ-XML, yanı sıra çünkü <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi aşağıdakileri yapmalıdır dahili olarak her çağrıldığında:  
  
-   Dizeyi belirteçlere çiğnemekten XPath ifadesi içeren dizeyi ayrıştırır.  
  
-   XPath ifadesi geçerli olduğundan emin olmak için belirteçlerini doğrular.  
  
-   Bir iç ifade ağacına ifadesine çevirir.  
  
-   Uygun şekilde ifade değerlendirmeye dayanarak sonuç kümesi için düğüm seçildikten düğümleri dolaşır.  
  
 Önemli ölçüde daha fazla XML sorgusu için karşılık gelen LINQ tarafından çalışmanın budur. Sorgu farklı türleri için belirli bir performans farkı değişir, ancak genel LINQ-XML sorguları daha az çalışma yapın ve bu nedenle, daha iyi kullanarak XPath ifadeleri değerlendirme görevlerini <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
