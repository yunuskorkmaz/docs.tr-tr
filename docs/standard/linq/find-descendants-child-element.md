---
title: Alt öğenin alt öğelerini bulma-LINQ to XML
description: 'Alt öğenin veya alt öğe dizisinin alt öğelerinin nasıl bulunacağını öğrenin. İki yöntem gösteriliyor: biri XPathEvaluate kullanır, diğeri LINQ to XML sorgu kullanır.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 675fb7da42f874e21374a6fbc4b61ae90a78caf2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552877"
---
# <a name="how-to-find-descendants-of-a-child-element-linq-to-xml"></a>Bir alt öğenin alt öğelerini bulma (LINQ to XML)

Bu makalede <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> , bir alt öğe dizisinin alt öğelerini bulmak için nasıl kullanılacağı ve aynı öğeleri bulmak için LINQ to XML sorgusunun nasıl kullanılacağı gösterilmektedir.

## <a name="example-find-all-the-text-descendant-elements-of-all-the-paragraph-elements"></a>Örnek: `Text` tüm öğelerin tüm alt öğelerini bulun `Paragraph`

Bu örnek, bir basit sözcük işleme belgesinin XML gösteriminden metin ayıklar. Önce tüm öğeleri seçer `Paragraph` , `Comment` öğesini yoksayar ve sonra `Text` her bir öğenin tüm alt öğelerini seçer `Paragraph` . Bu görevi iki şekilde yapar: ile <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> ve LINQ to XML sorgusuyla. Ardından sonuçları karşılaştırır ve özdeş olarak bulur.

XPath ifadesi  `./Paragraph//Text/text()` .

```csharp
XElement root = XElement.Parse(
@"<Root>
  <Paragraph>
    <Text>This is the start of</Text>
  </Paragraph>
  <Comment>
    <Text>This comment isn't part of the paragraph text.</Text>
  </Comment>
  <Paragraph>
    <Annotation Emphasis='true'>
      <Text> a sentence.</Text>
    </Annotation>
  </Paragraph>
  <Paragraph>
    <Text>  This is the second sentence.</Text>
  </Paragraph>
</Root>");

// LINQ to XML query
string str1 =
    root
    .Elements("Paragraph")
    .Descendants("Text")
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

// XPath expression
string str2 =
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))
    .Cast<XText>()
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

if (str1 == str2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(str2);
```

```vb
Dim root As XElement = _
    <Root>
        <Paragraph>
            <Text>This is the start of</Text>
        </Paragraph>
        <Comment>
            <Text>This comment isn't part of the paragraph text.</Text>
        </Comment>
        <Paragraph>
            <Annotation Emphasis='true'>
                <Text> a sentence.</Text>
            </Annotation>
        </Paragraph>
        <Paragraph>
            <Text>This is the second sentence.</Text>
        </Paragraph>
    </Root>

' LINQ to XML query
Dim str1 As String = _
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _
    Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

' XPath expression
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _
    .Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

If str1 = str2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(str2)
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Results are identical
This is the start of a sentence.  This is the second sentence.
```

## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
