---
title: XPath kullanarak LINQ to XML sorgulama-LINQ to XML
description: XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 8189bcdd38f9242a5890837633bbec4e7f2fc601
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553895"
---
# <a name="how-to-query-linq-to-xml-using-xpath-linq-to-xml"></a>XPath kullanarak LINQ to XML sorgulama (LINQ to XML)

Bu makale, XPath kullanarak bir XML ağacını sorgulamanızı sağlayan uzantı yöntemlerini tanıtır. Bu uzantı yöntemlerini kullanma hakkında ayrıntılı bilgi için bkz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> ..

> [!NOTE]
> Eski kodun kapsamlı kullanımı gibi XPath kullanarak sorgulamak için çok özel bir nedeniniz yoksa LINQ to XML ile XPath kullanılması önerilmez. XPath sorguları LINQ to XML sorguları da gerçekleştirmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek küçük bir XML ağacı oluşturur ve <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> bir öğe kümesi seçmek için kullanır.

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", 1),
    new XElement("Child1", 2),
    new XElement("Child1", 3),
    new XElement("Child2", 4),
    new XElement("Child2", 5),
    new XElement("Child2", 6)
);
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");
foreach (XElement el in list)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child1>2</Child1>
        <Child1>3</Child1>
        <Child2>4</Child2>
        <Child2>5</Child2>
        <Child2>6</Child2>
    </Root>

Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")
For Each el As XElement In list
    Console.WriteLine(el)
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Child2>4</Child2>
<Child2>5</Child2>
<Child2>6</Child2>
```
