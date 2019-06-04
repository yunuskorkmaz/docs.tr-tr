---
title: 'Nasıl yapılır: Bir alt öğesi (XPath-LINQ to XML) alt öğeleri bulma (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: a049ede1d533c4afc67892b7889debbe673e51c8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485475"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="f4a2f-102">Nasıl yapılır: Bir alt öğesi (XPath-LINQ to XML) alt öğeleri bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="f4a2f-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f4a2f-103">Bu konuda, belirli bir ada sahip bir alt öğenin alt öğeleri almak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="f4a2f-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="f4a2f-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="f4a2f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4a2f-105">Example</span></span>  
 <span data-ttu-id="f4a2f-106">Bu örnek, bir sözcük işleme belgesi bir XML gösteriminden metin ayıklama sorunları benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="f4a2f-107">Bu ilk tüm seçer `Paragraph` öğeleri ve ardından tüm seçer `Text` her alt öğeleri `Paragraph` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="f4a2f-108">Bu alt seçemiyorum `Text` öğelerini `Comment` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f4a2f-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
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
  
 <span data-ttu-id="f4a2f-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f4a2f-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  