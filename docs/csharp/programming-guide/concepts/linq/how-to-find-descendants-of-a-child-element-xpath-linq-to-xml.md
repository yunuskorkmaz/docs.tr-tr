---
title: Bir alt öğenin alt öğelerini bulma (XPath-LINQ to XML) (C#)
description: Bir XPath ifadesi kullanarak, belirli bir ada sahip bir alt öğenin alt öğelerini bulmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: b8e110abc2e0df99c3fdf6d2846c7cbbc4736c1a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303263"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="28755-103">Bir alt öğenin alt öğelerini bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="28755-103">How to find descendants of a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="28755-104">Bu konu başlığı altında, bir alt öğenin belirli bir ada sahip öğeleri nasıl alınacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28755-104">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="28755-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="28755-105">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="28755-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="28755-106">Example</span></span>  
 <span data-ttu-id="28755-107">Bu örnek, bir sözcük işleme belgesinin XML gösteriminden metin ayıklama sorunlarının benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="28755-107">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="28755-108">Önce tüm öğeleri seçer `Paragraph` ve ardından `Text` her bir öğenin tüm alt öğelerini seçer `Paragraph` .</span><span class="sxs-lookup"><span data-stu-id="28755-108">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="28755-109">Bu `Text` , öğesinin alt öğelerini seçmeyin `Comment` .</span><span class="sxs-lookup"><span data-stu-id="28755-109">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="28755-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="28755-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  