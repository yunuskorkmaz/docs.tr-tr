---
title: Statik olarak derlenen sorgular-LINQ to XML
description: LINQ to XML sorgularının statik olarak derlenerek XMLDocument üzerinden performans avantajı elde etme hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553414"
---
# <a name="statically-compiled-queries-linq-to-xml"></a>Statik olarak derlenen sorgular (LINQ to XML)

İle karşılaştırıldığında LINQ to XML en önemli performans avantajlarından biri <xref:System.Xml.XmlDocument> , LINQ to XML içindeki sorguların statik olarak derlenmesi, ancak XPath sorgularının çalışma zamanında yorumlanması gerekir. Bu özellik LINQ to XML yerleşik olarak bulunur, bu nedenle bundan faydalanmak için ek adımlar gerçekleştirmeniz gerekmez, ancak iki teknoloji arasında seçim yaparken farkın anlaşılması yararlı olur. Bu makalede fark açıklanır.

## <a name="statically-compiled-queries-vs-xpath"></a>Statik olarak derlenen sorgular ve XPath karşılaştırması

Aşağıdaki örnek, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir. Eşdeğer XPath ifadesi `//Address[@Type='Shipping']` .

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

Bu örnekteki sorgu ifadesi derleyici tarafından Yöntem tabanlı sorgu sözdizimine yeniden yazılır. Yöntem tabanlı sorgu sözdiziminde yazılan aşağıdaki örnek, öncekiyle aynı sonuçları üretir:

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<xref:System.Linq.Enumerable.Where%2A>Yöntemi bir genişletme yöntemidir. Daha fazla bilgi için bkz. [uzantı metotları (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/extension-methods.md). <xref:System.Linq.Enumerable.Where%2A>Bir genişletme yöntemi olduğundan, yukarıdaki sorgu aşağıdaki gibi yazılmış gibi derlenir:

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

Bu örnek, önceki iki örnekle tam olarak aynı sonuçları üretir. Bu, sorguların statik olarak bağlı yöntem çağrılarına etkin bir şekilde derlendiğini gösterir. Yineleyicilerin ertelenmiş yürütme semantiği ile birlikte, performansı geliştirir. Yineleyicilerin ertelenmiş yürütme semantiği hakkında daha fazla bilgi için bkz. [ertelenmiş yürütme ve yavaş değerlendirme](deferred-execution-lazy-evaluation.md).

> [!NOTE]
> Bu örnekler, derleyicinin yazabilmesi için kod temsilcisidir. Gerçek uygulama bu örneklerden biraz farklı olabilir, ancak bu örneklere benzer şekilde performans aynı olacaktır.

## <a name="executing-xpath-expressions-with-xmldocument"></a>XmlDocument ile XPath ifadeleri yürütme

Aşağıdaki örnek, <xref:System.Xml.XmlDocument> önceki örneklerle aynı sonuçları başarmak için kullanır:

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

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

Bu sorgu, LINQ to XML kullanan örneklerle aynı çıktıyı döndürür; Tek fark, LINQ to XML yazdırılan XML 'nin bu şekilde <xref:System.Xml.XmlDocument> girintilemez.

Ancak, <xref:System.Xml.XmlDocument> yaklaşım genellikle LINQ to XML, ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi her çağrıldığında aşağıdaki işlemleri yapması gerektiğinden, her zaman bir yaklaşım gerçekleştirmez:

- XPath ifadesini içeren dizeyi ayrıştırarak dizeyi belirteçlere bölmek.
- XPath ifadesinin geçerli olduğundan emin olmak için belirteçleri doğrulayın.
- İfadeyi bir iç ifade ağacına çevirin.
- İfadenin değerlendirmesine bağlı olarak, sonuç kümesi düğümlerini uygun şekilde seçerek düğümleri üzerinde yineleyin.

Bu, karşılık gelen LINQ to XML sorgusu tarafından gerçekleştirilen işin önemli ölçüde daha yüksektir. Belirli performans farkı farklı sorgu türleri için farklılık gösterir, ancak genel LINQ to XML sorgularında daha az iş olur ve bu nedenle, kullanarak XPath ifadelerini değerlendirmeden daha iyi gerçekleştirilir <xref:System.Xml.XmlDocument> .
