---
title: 'Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: 6905e6a7bd0cba37006b1fc3077ad72de36bcf56
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249946"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)
XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.  
  
 XPath ifadesi:  
  
 `//Category|//Price`  
  
 @No__t-0 standart sorgu işlecini kullanarak aynı sonuçları elde edebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek `Category` öğelerinin tümünü ve tüm `Price` öğelerini bulur ve bunları tek bir koleksiyona ekler. @No__t-0 sorgusunun sonuçları sıralamak için <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> çağırdığına unutmayın. XPath ifadesi değerlendirmesi sonuçları da belge sırasıyla bulunur.  
  
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
