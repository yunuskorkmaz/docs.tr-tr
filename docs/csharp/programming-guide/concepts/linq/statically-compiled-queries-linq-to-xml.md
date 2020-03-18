---
title: Statik Olarak Derlenen Sorgular (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253024"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Statik Olarak Derlenen Sorgular (LINQ - XML) (C#)
Linq'in XML'e en önemli performans <xref:System.Xml.XmlDocument>avantajlarından biri, Linq'ten XML'e sorguların statik olarak derlenmiş olması, XPath sorgularının ise çalışma zamanında yorumlanması gerektiğidir. Bu özellik LINQ'dan XML'e kadar yerleşiktir, bu nedenle bundan yararlanmak için ekstra adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken ayrımı anlamak yararlıdır. Bu konu farkı açıklar.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statik Olarak Derlenen Sorgular vs XPath  
 Aşağıdaki örnek, belirli bir ada sahip ve belirtilen değere sahip bir öznitelik ile soyundan gelen öğeleri nasıl elde etmek için gösterir.  
  
 Aşağıda eşdeğer XPath ifadesi veremistir:`//Address[@Type='Shipping']`
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnekteki sorgu ifadesi derleyici tarafından yöntem tabanlı sorgu sözdizimine yeniden yazılır. Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Yöntem <xref:System.Linq.Enumerable.Where%2A> bir uzantı yöntemidir. Daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın. Bir <xref:System.Linq.Enumerable.Where%2A> uzantı yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu, sorguların statik olarak bağlı yöntem çağrılarına etkili bir şekilde derlenmiş olduğu gerçeğini gösterir. Bu, yineleyicilerin ertelenmiş yürütme semantiği ile birlikte performansı artırır. Yineleyicilerin ertelenmiş yürütme semantikleri hakkında daha fazla bilgi için [LINQ'da XML'e (C#) Ertelenmiş Yürütme ve Tembel Değerlendirme bölümüne](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)bakın.  
  
> [!NOTE]
> Bu örnekler, derleyicinin yazabileceği kodu temsil eder. Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans bu örneklerle aynı veya benzer olacaktır.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument ile XPath İfadelerini Yürütme  
 Aşağıdaki örnek, <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları gerçekleştirmek için kullanır:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Bu sorgu, LINQ'u XML'e kullanan örneklerle aynı çıktıyı döndürür; tek fark, LinQ xml için yazılı XML girintisi, oysa <xref:System.Xml.XmlDocument> yok.  
  
 Ancak, <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlNode.SelectNodes%2A> yöntem her çağrıldığında dahili olarak aşağıdakileri yapmak gerekir, çünkü yaklaşım genellikle XML için LINQ gibi performans göstermez:  
  
- XPath ifadesini içeren dizeyi ayrışturarak dizeyi belirteçlere ayırır.  
  
- XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.  
  
- İfadeyi bir iç ifade ağacına çevirir.  
  
- İfadenin değerlendirilmesi temel alınarak sonuç kümesi için düğümleri uygun bir şekilde seçerek düğümleri yineler.  
  
 Bu, ilgili LINQ ile XML sorgusu nun yaptığı işten önemli ölçüde daha fazladır. Belirli performans farkı farklı sorgu türlerine göre değişir, ancak genel olarak LinQ'dan XML sorgularına daha az iş <xref:System.Xml.XmlDocument>yapar ve bu nedenle XPath ifadelerini kullanarak değerlendirmekten daha iyi performans gösterir.  
