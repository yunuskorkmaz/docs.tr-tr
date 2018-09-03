---
title: 'Nasıl yapılır: (XPath-LINQ to XML) iki konum yolunun birleşimini bulma (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: cd98c1da2f2f8653c5db36f89a63dfdc7a7ab691
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481347"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a>Nasıl yapılır: (XPath-LINQ to XML) iki konum yolunun birleşimini bulma (C#)
XPath birleşim iki XPath Konum yolları sonuçlarını bulmanıza olanak tanır.  
  
 XPath ifadesidir:  
  
 `//Category|//Price`  
  
 Kullanarak aynı sonucu elde edebileceğiniz <xref:System.Linq.Enumerable.Concat%2A> standart sorgu işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte tüm bulur `Category` öğeleri ve tüm `Price` öğeleri ve bunları tek bir koleksiyon birleştirir. Unutmayın [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu çağrıları <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sonuçları sıralamak için. Belge düzeninde XPath ifade değerlendirme sonuçlarını da var.  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
