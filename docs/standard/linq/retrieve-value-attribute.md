---
title: Bir özniteliğin değerini alma-LINQ to XML
description: Bir özniteliğin değerini alır. Bir XAttribute 'u istenen türe çevirebilirsiniz veya XAttribute. Value özelliğini kullanabilirsiniz.
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553875"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a>Öznitelik değerini alma (LINQ to XML)

Bu makale, özniteliklerin değerinin nasıl alınacağını gösterir. İki ana yol vardır: bir <xref:System.Xml.Linq.XAttribute> türü istenen türe çevirebilirsiniz; açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür. Alternatif olarak, özelliğini de kullanabilirsiniz <xref:System.Xml.Linq.XAttribute.Value%2A> . Ancak, atama genellikle daha iyi bir yaklaşımdır. Özniteliğini null yapılabilir bir değer türüne ayarlarsanız, kod, var olabilen veya var olabilen bir özniteliğin değeri alınırken yazmak daha basittir. Bu tekniğin örnekleri için bkz. [bir öğenin değerini alma](retrieve-value-element.md).

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a>Örnek: bir özniteliğin değerini almak için bir atama kullanın

C# içindeki bir özniteliğin değerini almak için, <xref:System.Xml.Linq.XAttribute> nesneyi istediğiniz türe atamalısınız. Visual Basic, değeri almak için tümleşik öznitelik özelliğini kullanabilirsiniz.

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a>Örnek: bir ad alanında olan XML 'den almak için bir tür dönüştürme kullanın

Aşağıdaki örnek, özniteliği bir ad alanında ise bir özniteliğin değerinin nasıl alınacağını gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>
        Dim str As String = root.@aw:Attr
        Console.WriteLine(str)
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
abcde
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
