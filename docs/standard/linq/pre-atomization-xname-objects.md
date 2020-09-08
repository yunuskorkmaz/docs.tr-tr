---
title: XName nesnelerinin ön cekmesi-LINQ to XML
description: Aynı ada sahip çok sayıda öğe oluştururken performansı artırmak için ayrılamaz 'i nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 97da1e09e246491d8427c7a69953e006c80475a4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553087"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml"></a>XName nesnelerinin (LINQ to XML) ön Atomonu

LINQ to XML performansını artırmanın bir yolu, önceden ayrılamaz <xref:System.Xml.Linq.XName> nesneleri kullanmaktır. Ön cekleştirme <xref:System.Xml.Linq.XName> , ve sınıflarının oluşturucularını kullanarak xml ağacını oluşturmadan önce bir nesneye bir dize atadığınız anlamına gelir <xref:System.Xml.Linq.XElement>  <xref:System.Xml.Linq.XAttribute> . Ardından, dizeden öğesine örtük dönüştürmeyi kullanan oluşturucuya bir dize geçirmek yerine, <xref:System.Xml.Linq.XName> başlatılan <xref:System.Xml.Linq.XName> nesneyi geçirirsiniz.

Bu, adları tekrarlandığı büyük bir XML ağacı oluşturduğunuzda performansı geliştirir. Bunu yapmak için, <xref:System.Xml.Linq.XName> XML ağacını oluşturmadan önce nesneleri bildirir ve başlatır ve sonra <xref:System.Xml.Linq.XName> öğe ve öznitelik adları için dizeleri belirtmek yerine nesneleri kullanın. Aynı ada sahip çok sayıda öğe veya öznitelik oluşturuyorsanız, bu teknik önemli performans artışı elde edebilir.

Kullanmanız gerekip gerekmediğini belirlemek için senaryolarınız ile önceden atomleştirme testi yapmanız gerekir.

## <a name="example-create-elements-in-various-ways-with-and-without-pre-atomization"></a>Örnek: öğeleri, ön atomleştirme olmadan ve çeşitli şekillerde oluşturun

Aşağıdaki örnek, ön atomını gösterir.

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

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

Aşağıdaki örnek, bir ad alanındaki bir XML belgesi için aynı tekniği gösterir:

```csharp
XNamespace aw = "http://www.adventure-works.com";
XName Root = aw + "Root";
XName Data = aw + "Data";
XName ID = "ID";

XElement root = new XElement(Root,
    new XAttribute(XNamespace.Xmlns + "aw", aw),
    new XElement(Data,
        new XAttribute(ID, "1"),
        "4,100,000"),
    new XElement(Data,
        new XAttribute(ID, "2"),
        "3,700,000"),
    new XElement(Data,
        new XAttribute(ID, "3"),
        "1,150,000")
);

Console.WriteLine(root);
```

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

```csharp
XName Root = "Root";
XName Data = "Data";
XName ID = "ID";

DateTime t1 = DateTime.Now;
XElement root = new XElement(Root,
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement(Data,
        new XAttribute(ID, i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

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

```csharp
DateTime t1 = DateTime.Now;
XElement root = new XElement("Root",
    from i in System.Linq.Enumerable.Range(1, 100000)
    select new XElement("Data",
        new XAttribute("ID", i),
        i * 5)
);
DateTime t2 = DateTime.Now;

Console.WriteLine("Time to construct:{0}", t2 - t1);
```

```vb
Dim sw As Stopwatch = Stopwatch.StartNew()
Dim root As New XElement("Root", From i In Enumerable.Range(1, 100000)
                                 Select New XElement("Data", New XAttribute("ID", i), i * 5))
sw.Stop()
Console.WriteLine($"Time to construct: {sw.ElapsedMilliseconds} milliseconds")
```

## <a name="see-also"></a>Ayrıca bkz.

- [Atomlanmış XName ve XNamespace nesneleri](atomized-xname-xnamespace-objects.md)
