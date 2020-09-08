---
title: Varsayılan ad alanları kapsamı-LINQ to XML
description: XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir. Bu, doğru ve hatalı şekilde sorgulamada yanlış yollar sunar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553934"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a>Varsayılan ad alanlarının kapsamı (LINQ to XML)

XML ağacında temsil edilen varsayılan ad alanları sorgular kapsamında değildir. Varsayılan bir ad alanında olan XML varsa, sorguda kullanılacak nitelikli bir ad oluşturmak için ad alanını yerel adla birleştirmeniz gerekir.

Varsayılan ad alanı olan bir XML ağacını sorgularken yaygın bir hata, XML 'nin bir ad alanında olmadığı gibi sorguyu yazmaktır. İlk örnekte, varsayılan bir ad alanının tipik hatalı bir sorgusu gösterilmektedir. İkincisi, doğru bir sorgu gösterir.

## <a name="example-improper-query-of-xml-in-a-namespace"></a>Örnek: bir ad alanında hatalı XML sorgusu

Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren yanlış bir sorguyu gösterir.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a>Örnek: bir ad alanında XML 'nin doğru sorgusu

Bu örnekte, bir ad alanında XML oluşturulması ve uygun bir sorgu gösterilmektedir.

C# ' de, doğru yaklaşım bir nesneyi bildirmek ve başlatmak <xref:System.Xml.Linq.XNamespace> ve nesneleri belirtirken kullanmak <xref:System.Xml.Linq.XName> . Bu durumda, yöntemin bağımsız değişkeni <xref:System.Xml.Linq.XContainer.Elements%2A> bir <xref:System.Xml.Linq.XName> nesnedir.

Visual Basic kullanırken doğru yaklaşım, genel bir varsayılan ad alanını bildirmek ve başlatmak. Bu, tüm XML özelliklerini varsayılan ad alanına koyar.

Kod aşağıdaki gibidir:

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
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış](namespaces-overview.md)
