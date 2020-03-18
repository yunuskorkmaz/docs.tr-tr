---
title: Bir alt öğenin torunları (XPath-LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: fb3e20ce21c1f6d2a71f2f71b8acec7cecf0f3ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141101"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Bir alt öğenin torunları (XPath-LINQ - XML) (C#)
Bu konu, belirli bir ada sahip bir alt öğenin soyundan gelen öğeleri nasıl elde etmek için gösterir.  
  
 XPath ifadesi:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir sözcük işleme belgesinin XML gösteriminden metin ayıklama sorunlarını simüle eder. Önce tüm `Paragraph` öğeleri seçer ve sonra her `Text` `Paragraph` öğenin tüm soyundan öğeleri seçer. Bu, öğenin soyundan gelen `Text` öğeleri seçmez. `Comment`  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  