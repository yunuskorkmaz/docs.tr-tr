---
title: Statik olarak derlenen sorgular (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253024"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Statik olarak derlenen sorgular (LINQ to XML)C#()
En önemli performans avantajlarından biri de LINQ to XML <xref:System.Xml.XmlDocument>, LINQ to XML içindeki sorguların statik olarak derlenmesine karşın XPath sorgularının çalışma zamanında yorumlanması gerekir. Bu özellik LINQ to XML ' de yerleşiktir. bu nedenle, bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur. Bu konu, farkı açıklamaktadır.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenen sorgular ve XPath  
 Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.  
  
 Eşdeğer XPath ifadesi aşağıda verilmiştir:`//Address[@Type='Shipping']`
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu söz dizimine yeniden yazılır. Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Yöntemi bir genişletme yöntemidir. Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md). Bir <xref:System.Linq.Enumerable.Where%2A> genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir. Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir. Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [LINQ to XMLC#() içinde ertelenmiş yürütme ve geç değerlendirme](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
> Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir. Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans aynı veya bu örneklere benzer olacaktır.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument ile XPath Ifadeleri yürütme  
 Aşağıdaki örnek, önceki <xref:System.Xml.XmlDocument> örneklerle aynı sonuçları başarmak için kullanır:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin girintilebilirken <xref:System.Xml.XmlDocument> , bunun farklılığı değildir.  
  
 Ancak, <xref:System.Xml.XmlNode.SelectNodes%2A> yaklaşım genellikle LINQ to XML, ve yöntemi her çağrıldığında aşağıdaki işlemleri yapması gerektiğinden, her zaman yaklaşım uygulanmaz: <xref:System.Xml.XmlDocument>  
  
- XPath ifadesini içeren dizeyi ayrıştırır ve dizeyi belirteçlere ayırır.  
  
- XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.  
  
- İfadeyi bir iç ifade ağacına çevirir.  
  
- İfadenin değerlendirmesine bağlı olarak sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde dolaşır.  
  
 Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir. Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş olur ve bu nedenle, kullanarak <xref:System.Xml.XmlDocument>XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir.  
