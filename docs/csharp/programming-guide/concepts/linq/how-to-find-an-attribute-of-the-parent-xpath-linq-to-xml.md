---
title: 'Nasıl yapılır: Bulma (XPath-LINQ to XML) üst özniteliği (C#)'
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: d6660e2bab074432f3dcd8f95825d76a6ff704a5
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487399"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>Nasıl yapılır: Bulma (XPath-LINQ to XML) üst özniteliği (C#)
Bu konuda, üst öğeye gidin ve bir özniteliğin bulmak gösterilmektedir.  
  
 XPath ifadesidir:  
  
 `../@id`  
  
## <a name="example"></a>Örnek  
 Bu örnekte ilk bulur bir `Author` öğesi. Ardından bulduğu `id` üst öğesinin özniteliği.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Results are identical  
id="bk101"  
```  
  
