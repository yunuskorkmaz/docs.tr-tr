---
title: 'Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: ebb2ddc3a7ba5e08e99cecca01294e5ad3182e8b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253854"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (C#)
XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.  
  
 XPath ifadesi:  
  
 `//Category|//Price`  
  
 <xref:System.Linq.Enumerable.Concat%2A> Standart sorgu işlecini kullanarak aynı sonuçları elde edebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek tüm `Category` öğeleri ve tüm `Price` öğeleri bulur ve bunları tek bir koleksiyona ekler. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Sorgunun sonuçları sıralamak için çağrı <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> yaptığı unutulmamalıdır. XPath ifadesi değerlendirmesi sonuçları da belge sırasıyla bulunur.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  