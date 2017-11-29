---
title: "Nasıl yapılır: Bul (XPath-LINQ-XML) alt öğenin alt öğeleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 873cfe6a725a932ac4616e7ccf0ea11e3f6479f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="54d09-102">Nasıl yapılır: Bul (XPath-LINQ-XML) alt öğenin alt öğeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="54d09-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="54d09-103">Bu konuda, belirli bir ada sahip bir alt öğenin alt öğelerini alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="54d09-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="54d09-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="54d09-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="54d09-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="54d09-105">Example</span></span>  
 <span data-ttu-id="54d09-106">Bu örnek bir sözcük işleme belgesini XML gösteriminden metin ayıklama sorunları benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="54d09-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="54d09-107">Bu ilk tüm seçer `Paragraph` öğeleri ve ardından seçer tüm `Text` her alt öğeleri `Paragraph` öğesi.</span><span class="sxs-lookup"><span data-stu-id="54d09-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="54d09-108">Bu alt öğesi seçin değil `Text` öğeleri `Comment` öğesi.</span><span class="sxs-lookup"><span data-stu-id="54d09-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="54d09-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="54d09-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="54d09-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54d09-110">See Also</span></span>  
 [<span data-ttu-id="54d09-111">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="54d09-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
