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
# <a name="how-to-find-descendants-of-a-child-element-linq-to-xml"></a><span data-ttu-id="320d0-104">Bir alt öğenin alt öğelerini bulma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="320d0-104">How to find descendants of a child element (LINQ to XML)</span></span>

<span data-ttu-id="320d0-105">Bu makalede <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> , bir alt öğe dizisinin alt öğelerini bulmak için nasıl kullanılacağı ve aynı öğeleri bulmak için LINQ to XML sorgusunun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="320d0-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the descendant elements of a sequence of child elements, and how to use LINQ to XML query to find the same elements.</span></span>

## <a name="example-find-all-the-text-descendant-elements-of-all-the-paragraph-elements"></a><span data-ttu-id="320d0-106">Örnek: `Text` tüm öğelerin tüm alt öğelerini bulun `Paragraph`</span><span class="sxs-lookup"><span data-stu-id="320d0-106">Example: Find all the `Text` descendant elements of all the `Paragraph` elements</span></span>

<span data-ttu-id="320d0-107">Bu örnek, bir basit sözcük işleme belgesinin XML gösteriminden metin ayıklar.</span><span class="sxs-lookup"><span data-stu-id="320d0-107">This example extracts text from an XML representation of a simple word processing document.</span></span> <span data-ttu-id="320d0-108">Önce tüm öğeleri seçer `Paragraph` , `Comment` öğesini yoksayar ve sonra `Text` her bir öğenin tüm alt öğelerini seçer `Paragraph` .</span><span class="sxs-lookup"><span data-stu-id="320d0-108">It first selects all `Paragraph` elements, ignoring the `Comment` element, and then it selects all the `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="320d0-109">Bu görevi iki şekilde yapar: ile <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> ve LINQ to XML sorgusuyla.</span><span class="sxs-lookup"><span data-stu-id="320d0-109">It does this task in two ways: with <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> and with LINQ to XML query.</span></span> <span data-ttu-id="320d0-110">Ardından sonuçları karşılaştırır ve özdeş olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="320d0-110">It then compares the results and finds them identical.</span></span>

<span data-ttu-id="320d0-111">XPath ifadesi  `./Paragraph//Text/text()` .</span><span class="sxs-lookup"><span data-stu-id="320d0-111">The XPath expression is  `./Paragraph//Text/text()`.</span></span>

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

<span data-ttu-id="320d0-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="320d0-112">This example produces the following output:</span></span>

```output
Results are identical
This is the start of a sentence.  This is the second sentence.
```

## <a name="see-also"></a><span data-ttu-id="320d0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="320d0-113">See also</span></span>

- [<span data-ttu-id="320d0-114">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="320d0-114">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
