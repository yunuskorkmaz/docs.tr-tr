---
title: Sorgular (LINQ to XML)'statik olarak derlenmiş (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: ee5d5fbc9bf2aa90635e75c5c8cbf52b16e3f349
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483466"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Sorgular (LINQ to XML)'statik olarak derlenmiş (C#)
En önemli performans birini avantajlar LINQ, XML olarak <xref:System.Xml.XmlDocument>, XPath sorguları çalışma zamanında yorumlanacağını ancak LINQ to XML sorgularında statik olduğunu, derlenir. Bu özellik için LINQ to XML, yararlanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknolojiyi arasında seçim yaparken, aradaki farkı kavramak yararlıdır yerleşik olarak bulunur. Bu konu, farkı açıklar.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenmiş sorgular vs. XPath  
 Aşağıdaki örnek belirtilen ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğeleri almak nasıl gösterir.  
  
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
  
 Bu örnekte sorgu ifadesi metot tabanlı sorgu söz dizimi için derleyici tarafından yeniden yazılır. Metot tabanlı sorgu söz dizimi içinde yazılır, aşağıdaki örnekte, önceki'dekiyle aynı sonucu üretir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Bir genişletme yöntemi bir yöntemdir. Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Çünkü <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemi, yukarıdaki sorgunun yazılmış gibi sorgulamanıza şu şekilde derlenir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu sorgular, statik olarak bağlı yöntemi çağrılarını etkili bir şekilde derlenir olgu gösterilmektedir. Bu, yineleyiciler, ertelenmiş yürütme semantikleri ile birleştirilmiş performansını artırır. Yineleyiciler ertelenmiş yürütme semantikleri hakkında daha fazla bilgi için bkz. [ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Bu örnekler derleyici yazabilirsiniz kodun temsilcisi. Gerçek uygulamalar bu örneklerden biraz farklı olabilir, ancak performans aynı olacaktır ya da bu örneklerde benzer.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XPath ifadeleri XmlDocument ile çalıştırma  
 Aşağıdaki örnekte <xref:System.Xml.XmlDocument> önceki örnekler aynı sonuçlara ulaşmak için:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Bu sorgu, LINQ to XML kullanan örnekler aynı çıkışı döndürür; tek fark LINQ to XML yazdırılan XML girintiler takvimidir <xref:System.Xml.XmlDocument> desteklemez.  
  
 Ancak, <xref:System.Xml.XmlDocument> yaklaşımı genellikle gerçekleştirmez LINQ to XML, yanı sıra çünkü <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi aşağıdakileri yapmalıdır dahili olarak her çağrıldığında:  
  
- Bu dizeyi belirteçlere bozucu bir XPath ifadesi içeriyor dizeyi ayrıştırır.  
  
- Bu XPath ifadesi geçerli olduğundan emin olmak için belirteçlerini doğrular.  
  
- Bu iç ifade ağacı ifadeye çevrilir.  
  
- Uygun şekilde ifade değerlendirmeye göre sonuç kümesi için düğümleri seçme düğümleri aracılığıyla yinelenir.  
  
 Önemli ölçüde daha fazla ilgili LINQ to XML sorgusu ile çalışmanın budur. Sorgu farklı türleri için belirli bir performans farkı değişir, ancak genel bir LINQ to XML sorguları daha az çalışma yapın ve bu nedenle, daha iyi kullanarak XPath ifadelerini değerlendirme gerçekleştirmek <xref:System.Xml.XmlDocument>.  
  