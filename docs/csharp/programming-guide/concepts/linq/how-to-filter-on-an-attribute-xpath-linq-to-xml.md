---
title: Bir öznitelik te filtreleme (XPath-LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: ab2cd439f4dd1454de4fa565658ef5dac14b8c22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141281"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-c"></a>Bir öznitelik te filtreleme (XPath-LINQ - XML) (C#)
Bu konu, belirli bir ada sahip soyundan gelen öğelerin nasıl alınıldığını ve belirli bir değere sahip bir öznitelik ile nasıl alınılsüreceğini gösterir.  
  
 XPath ifadesi:  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a>Örnek  
 Bu örnek, "Sevkiyat" değeri `Address`ne kadar `Type` öznitelik taşıyan tüm soyundan gelen öğeleri bulur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements(".//Address[@Type='Shipping']");  
  
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
