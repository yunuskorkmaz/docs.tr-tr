---
title: Ad alanlarında XML üzerinde sorgu yazma-LINQ to XML
description: Bir ad alanında bulunan XML üzerinde bir sorgu yazmak için, doğru ad alanına sahip XName nesnelerini kullanırsınız. Bunu C# ve Visual Basic ve sorgu oluşturma hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 7d2c765c30409b019bf4723b9161c577e2074c04
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553028"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-linq-to-xml"></a>Ad alanlarında XML üzerinde sorgu yazma (LINQ to XML)

Bir ad alanında bulunan XML üzerinde bir sorgu yazmak için, <xref:System.Xml.Linq.XName> doğru ad alanına sahip nesneleri kullanmanız gerekir.

C# için en yaygın yaklaşım, <xref:System.Xml.Linq.XNamespace> URI 'yi içeren bir dize kullanarak başlatmak, ardından ad alanını yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanmaktır.

Visual Basic için en yaygın yaklaşım genel bir ad alanı tanımlamaktır ve sonra genel ad alanını kullanan XML değişmez değerlerini ve XML özelliklerini kullanır. Genel bir varsayılan ad alanı tanımlayabilirsiniz. Bu durumda, XML sabit değerlerinde bulunan öğeler varsayılan olarak ad alanında yer alabilir. Alternatif olarak, ön ek içeren bir genel ad alanı tanımlayabilir ve sonra öneki XML sabit değerlerinde ve XML özelliklerinde gereken şekilde kullanabilirsiniz. Diğer XML formlarında olduğu gibi, özniteliklerin her zaman varsayılan olarak ad alanı yoktur.

Bu makaledeki ilk örnekte, varsayılan bir ad alanında bir XML ağacının nasıl oluşturulacağı gösterilmektedir. İkincisi, bir ad alanında öneki olan bir XML ağacının nasıl oluşturulacağını gösterir.

## <a name="example-create-a-tree-in-a-default-namespace-and-retrieve-elements"></a>Örnek: varsayılan bir ad alanında ağaç oluşturma ve öğeleri alma

Aşağıdaki örnek, varsayılan bir ad alanında olan bir XML ağacı oluşturur ve ardından bir öğe koleksiyonu alır.

```csharp
XNamespace aw = "http://www.adventure-works.com";
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
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
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
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
1
2
3
```

## <a name="example-create-a-tree-in-a-namespace-with-a-prefix-and-retrieve-elements"></a>Örnek: bir ad alanında önek ve alma öğeleri içeren bir ağaç oluşturma

C# ' ta, ön ek içeren bir ad alanı kullanan bir XML ağacına veya varsayılan bir ad alanı olan bir XML ağacına sorgu yazarken aynı şekilde sorgular yazarsınız.

Aşağıdaki örnek, öneki olan bir ad alanında bulunan bir XML ağacı oluşturur ve ardından bir öğe koleksiyonu alır.

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
    <aw:Child>1</aw:Child>
    <aw:Child>2</aw:Child>
    <aw:Child>3</aw:Child>
    <aw:AnotherChild>4</aw:AnotherChild>
    <aw:AnotherChild>5</aw:AnotherChild>
    <aw:AnotherChild>6</aw:AnotherChild>
</aw:Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>1</aw:Child>
                <aw:Child>2</aw:Child>
                <aw:Child>3</aw:Child>
                <aw:AnotherChild>4</aw:AnotherChild>
                <aw:AnotherChild>5</aw:AnotherChild>
                <aw:AnotherChild>6</aw:AnotherChild>
            </aw:Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<aw:Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
1
2
3
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış](namespaces-overview.md)
