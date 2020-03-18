---
title: İki konum yolunun birleşimi (XPath-LINQ - XML) (C#) nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 17a3310f367cb68b3b80b1a3f30af40428f6d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141215"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>İki konum yolunun birleşimi (XPath-LINQ - XML) (C#) nasıl bulabilirim?
XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.  
  
 XPath ifadesi:  
  
 `//Category|//Price`  
  
 Standart sorgu işleci kullanarak <xref:System.Linq.Enumerable.Concat%2A> aynı sonuçları elde edebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, tüm `Category` öğeleri ve `Price` tüm öğeleri bulur ve bunları tek bir koleksiyona dönüştürür. Sorgunun [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sonuçları <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sıralamak için çağırdığına dikkat edin. XPath ifade değerlendirme sonuçları da belge sırasına göre.  
  
 Bu örnekte aşağıdaki XML belgesi kullanılır: [Örnek XML Dosyası: Sayısal Veriler (LINQ-XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
  