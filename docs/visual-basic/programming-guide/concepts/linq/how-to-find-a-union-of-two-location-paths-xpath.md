---
title: 'Nasıl yapılır: İki Konum Yolunun Birleşimini Bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 36528d1748d5675231f14de92dcd78734a696711
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406878"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)
XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.  
  
 XPath ifadesi:  
  
 `//Category|//Price`  
  
 Standart sorgu işlecini kullanarak aynı sonuçları elde edebilirsiniz <xref:System.Linq.Enumerable.Concat%2A> .  
  
## <a name="example"></a>Örnek  
 Bu örnek tüm `Category` öğeleri ve tüm `Price` öğeleri bulur ve bunları tek bir koleksiyona ekler. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Sorgunun <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sonuçları sıralamak için çağrı yaptığı unutulmamalıdır. XPath ifadesi değerlendirmesi sonuçları da belge sırasıyla bulunur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](linq-to-xml-for-xpath-users.md)
