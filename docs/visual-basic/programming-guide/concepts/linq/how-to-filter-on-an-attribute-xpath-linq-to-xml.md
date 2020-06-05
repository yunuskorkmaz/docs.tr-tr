---
title: 'Nasıl yapılır: Öznitelik Filtreleme (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: ffefb9d6-45ec-4677-a396-dd9c2b36298f
ms.openlocfilehash: 5bc0a621f0d3bb8e22701440383cdac54c7be51b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394511"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: bir özniteliğe filtre uygulama (XPath-LINQ to XML) (Visual Basic)
Bu konu, belirtilen bir ada sahip ve belirtilen değere sahip bir öznitelik ile alt öğelerin nasıl alınacağını gösterir.  
  
 XPath ifadesi:  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a>Örnek  
 Bu örnek, adı olan tüm alt öğeleri `Address` ve `Type` "Shipping" değeri olan bir özniteliği bulur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In po...<Address> _  
    Where el.@Type = "Shipping" _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    po.XPathSelectElements(".//Address[@Type='Shipping']")  
  
If (list1.Count = list2.Count And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
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
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XPath kullanıcıları için LINQ to XML (Visual Basic)](linq-to-xml-for-xpath-users.md)
