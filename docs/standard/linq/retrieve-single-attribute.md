---
title: Tek bir özniteliği alma-LINQ to XML
description: Öznitelik adı verilen bir öğenin tek bir özniteliğini alın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553878"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a>Tek bir özniteliği alma (LINQ to XML)

Bu makalede, öznitelik adı verildiğinde bir öğenin tek bir özniteliği nasıl alınır açıklanmaktadır. Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.

<xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> Sınıfının yöntemi, <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip öğesini döndürür.

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a>Örnek: öğe ve öznitelik adları verilen öznitelik değerlerini alın

Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> adlı bir öğe oluşturmak için yöntemini kullanır `PhoneNumbers` . Ardından adlı tüm alt öğeleri bulur `Phone` ve her biri için, <xref:System.Xml.Linq.XElement.Attribute%2A> adlı özniteliğin değerini almak ve çıkarmak için yöntemini kullanır `type` :

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a>Örnek: bir atama ile öznitelik değeri alma

Bir özniteliğin değerini, nesneleri ile yaptığınız gibi, kaldırarak alabilirsiniz <xref:System.Xml.Linq.XElement> . Aşağıdaki örnek şunu gösterir:

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
home
work
```

LINQ to XML,,,,,,,,,,,,,, <xref:System.Xml.Linq.XAttribute> `string` `bool` `bool?` `int` `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` `float?` `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,,,,,,, ve

## <a name="example-cast-for-an-attribute-in-a-namespace"></a>Örnek: ad alanındaki bir öznitelik için atama

Aşağıdaki örnek, bir ad alanında olan bir öznitelik için aynı kodu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
home
work
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
