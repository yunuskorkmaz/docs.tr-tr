---
title: Boş sorgu sonuçları kümelerinde hata ayıklama-LINQ to XML
description: Varsayılan bir ad alanında bir XML ağacını sorguladığınızda, XML 'nin bir ad alanında olmamasına rağmen, yaygın olarak sorgulanmasını önleyin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 8fc6b1a80b183f8e2b0f80fc554a12c2657dcb55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557144"
---
# <a name="how-to-debug-empty-query-results-sets-linq-to-xml"></a>Boş sorgu sonuçları kümelerinde hata ayıklama (LINQ to XML)

XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.

Bu makaledeki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği ve daha sonra yanlış sorgulandığı tipik bir yöntemi gösterir.

İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.

Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).

## <a name="example-an-improper-query-on-xml-in-a-namespace"></a>Örnek: bir ad alanında XML üzerinde hatalı sorgu

Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

Örnek bu sonucu üretir:

```output
Result set follows:
End of result set
```

## <a name="example-a-proper-query-on-xml-in-a-namespace"></a>Örnek: bir ad alanında XML üzerinde doğru bir sorgu

Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.

Çözüm, bir nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XNamespace> ve nesneleri belirtirken kullanmak <xref:System.Xml.Linq.XName> . Bu durumda, yöntemin bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> bir <xref:System.Xml.Linq.XName> nesnedir.

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

Örnek bu sonucu üretir:

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>Ayrıca bkz.

- [Temel sorgular (LINQ to XML) (Visual Basic)](./find-element-specific-attribute.md)
