---
title: Statik olarak derlenen sorgular (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f295e8aa8b747b90933d6a35e5352f66740ef071
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582914"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Statik olarak derlenen sorgular (LINQ to XML) (Visual Basic)

@No__t_0 aksine LINQ to XML en önemli performans avantajlarından biri, LINQ to XML sorguların statik olarak derlenmesine karşın XPath sorgularının çalışma zamanında yorumlanması gerekir. Bu özellik LINQ to XML ' de yerleşiktir. bu nedenle, bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur. Bu konu, farkı açıklamaktadır.

## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenen sorgular ve XPath karşılaştırması

Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.

Eşdeğer XPath ifadesi aşağıda verilmiştir:

```vb
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

Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu söz dizimine yeniden yazılır. Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

@No__t_0 yöntemi bir genişletme yöntemidir. Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). @No__t_0 bir genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir. Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir. Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

> [!NOTE]
> Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir. Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak performans aynı veya bu örneklere benzer olacaktır.

## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument ile XPath Ifadeleri yürütme

Aşağıdaki örnek, önceki örneklerle aynı sonuçları başarmak için <xref:System.Xml.XmlDocument> kullanır:

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

Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin girintilebilirken <xref:System.Xml.XmlDocument> değildir.

Ancak, <xref:System.Xml.XmlDocument> yaklaşımı genellikle LINQ to XML ve <xref:System.Xml.XmlNode.SelectNodes%2A> yönteminin her çağrılışında aşağıdakileri yapması gerektiğinden, her zaman bir şekilde gerçekleştirmez:

- XPath ifadesini içeren dizeyi ayrıştırır ve dizeyi belirteçlere ayırır.

- XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrular.

- İfadeyi bir iç ifade ağacına çevirir.

- İfadenin değerlendirmesine bağlı olarak sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde dolaşır.

Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir. Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş yapılır ve bu nedenle, <xref:System.Xml.XmlDocument> kullanarak XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
