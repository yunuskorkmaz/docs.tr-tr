---
title: Parçalara Ayırma Öncesi XName Nesneleri (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: c0e75afa797d2b20f32fc55e6c19d0c1593d174c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740785"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>XName nesnelerinin (LINQ to XML) ön atomda (Visual Basic)

LINQ to XML performansını artırmanın bir yolu, önceden ayrılamaz <xref:System.Xml.Linq.XName> nesneleri kullanmaktır. Ön cekleştirme, <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> sınıflarının oluşturucularını kullanarak XML ağacını oluşturmadan önce bir <xref:System.Xml.Linq.XName> nesnesine bir dize atamanız anlamına gelir. Sonra, dizeden <xref:System.Xml.Linq.XName>örtük dönüştürmeyi kullanan oluşturucuya bir dize geçirmek yerine, başlatılan <xref:System.Xml.Linq.XName> nesnesini geçirirsiniz.

Bu, belirli adların tekrarlandığı büyük bir XML ağacı oluşturduğunuzda performansı geliştirir. Bunu yapmak için, XML ağacını oluşturmadan önce <xref:System.Xml.Linq.XName> nesneleri bildirip başlatın ve ardından öğe ve öznitelik adları için dizeleri belirtmek yerine <xref:System.Xml.Linq.XName> nesneleri kullanın. Aynı ada sahip çok sayıda öğe (veya öznitelik) oluşturuyorsanız bu teknik önemli performans artışı elde edebilir.

Kullanmanız gerekip gerekmediğini belirlemek için senaryolarınız ile önceden atomleştirme testi yapmanız gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek şunu gösterir:

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Data ID="1">4,100,000</Data>
  <Data ID="2">3,700,000</Data>
  <Data ID="3">1,150,000</Data>
</Root>
```

Aşağıdaki örnek, XML belgesinin bir ad alanında bulunduğu tekniği gösterir:

```vb
Dim aw As XNamespace = "http://www.adventure-works.com"
Dim root1 As XName = aw + "Root"
Dim data As XName = aw + "Data"
Dim id As XName = "ID"

Dim root2 As New XElement(root1, New XAttribute(XNamespace.Xmlns + "aw", aw),
                          New XElement(data, New XAttribute(id, "1"), "4,100,000"),
                          New XElement(data, New XAttribute(id, "2"), "3,700,000"),
                          New XElement(data, New XAttribute(id, "3"), "1,150,000"))

Console.WriteLine(root2)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Data ID="1">4,100,000</aw:Data>
  <aw:Data ID="2">3,700,000</aw:Data>
  <aw:Data ID="3">1,150,000</aw:Data>
</aw:Root>
```

Aşağıdaki örnek, gerçek dünyada büyük olasılıkla karşılaşacağınız şekilde daha benzerdir. Bu örnekte, öğesinin içeriği bir sorgu tarafından sağlanır:

```vb
Dim root1 As XName = "Root"
Dim data As XName = "Data"
Dim id As XName = "ID"
  
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root2 As New XElement(root1, From i In Enumerable.Range(1, 100000)
                                 Select New XElement(data, New XAttribute(ID, i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```  

Önceki örnek, şu örnekteki adların ön cede olmadığı bir daha iyi şekilde çalışır:

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
- [Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)](atomized-xname-and-xnamespace-objects-linq-to-xml.md)
