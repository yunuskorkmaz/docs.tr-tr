---
title: 'Nasıl yapılır: Alt öğenin alt öğelerini bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: f17d723aa03c45daa4e7e741ea6b14c637537ccf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253711"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="58d43-102">Nasıl yapılır: Alt öğenin alt öğelerini bul (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="58d43-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="58d43-103">Bu konu başlığı altında, bir alt öğenin belirli bir ada sahip öğeleri nasıl alınacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58d43-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="58d43-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="58d43-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="58d43-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="58d43-105">Example</span></span>  
 <span data-ttu-id="58d43-106">Bu örnek, bir sözcük işleme belgesinin XML gösteriminden metin ayıklama sorunlarının benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="58d43-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="58d43-107">Önce tüm `Paragraph` öğeleri seçer ve ardından her `Paragraph` bir öğenin tüm `Text` alt öğelerini seçer.</span><span class="sxs-lookup"><span data-stu-id="58d43-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="58d43-108">Bu, `Text` `Comment` öğesinin alt öğelerini seçmeyin.</span><span class="sxs-lookup"><span data-stu-id="58d43-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="58d43-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="58d43-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  