---
title: Öznitelik koleksiyonu alma-LINQ to XML
description: Bir öğenin özniteliklerini almak için XElement. Attributes metodunu nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: a15375ffd6b3af7fb9119e3321495cffa00268e4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553070"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml"></a>Öznitelik koleksiyonunu alma (LINQ to XML)

Bu makalede, <xref:System.Xml.Linq.XElement.Attributes%2A> bir öğenin özniteliklerini almak için yönteminin kullanımı gösterilmektedir.

## <a name="example-iterate-through-the-attributes-of-an-element"></a>Örnek: bir öğenin öznitelikleri arasında yineleme

Aşağıdaki örnek, bir öğenin özniteliklerinin toplanması arasında nasıl yineleme yapılacağını gösterir.

```csharp
XElement val = new XElement("Value",
    new XAttribute("ID", "1243"),
    new XAttribute("Type", "int"),
    new XAttribute("ConvertableTo", "double"),
    "100");
IEnumerable<XAttribute> listOfAttributes =
    from att in val.Attributes()
    select att;
foreach (XAttribute a in listOfAttributes)
    Console.WriteLine(a);
```

```vb
Dim val = _
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>
Dim listOfAttributes As IEnumerable(Of XAttribute) = _
    From att In val.Attributes() _
    Select att
For Each att As XAttribute In listOfAttributes
    Console.WriteLine(att)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
ID="1243"
Type="int"
ConvertableTo="double"
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
