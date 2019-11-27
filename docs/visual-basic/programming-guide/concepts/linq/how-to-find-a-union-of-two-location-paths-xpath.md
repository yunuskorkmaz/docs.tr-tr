---
title: 'Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: db9ba3f66bfa8643738203ec05a106bab4193fda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352980"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)
XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.  
  
 XPath ifadesi:  
  
 `//Category|//Price`  
  
 Aynı sonuçları, <xref:System.Linq.Enumerable.Concat%2A> standart sorgu işlecini kullanarak elde edebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, tüm `Category` öğelerini ve tüm `Price` öğeleri bulur ve bunları tek bir koleksiyona ekler. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgusunun sonuçları sıralamak için <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> çağırdığına unutmayın. XPath ifadesi değerlendirmesi sonuçları da belge sırasıyla bulunur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
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

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
