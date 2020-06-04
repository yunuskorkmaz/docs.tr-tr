---
title: 'Nasıl yapılır: Belirli Bir Özniteliğe Sahip Öğeyi Bulma'
ms.date: 07/20/2015
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
ms.openlocfilehash: ec5d3bf46d517e2cfb27c228674d9b86fefffa14
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405254"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a>Nasıl yapılır: belirli bir özniteliğe sahip bir öğe bulma (Visual Basic)
Bu konu, belirli bir değere sahip bir özniteliğe sahip olan bir öğenin nasıl bulunacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Örnek, `Address` `Type` "Faturalandırma" değerine sahip bir özniteliğe sahip olan öğenin nasıl bulunacağını gösterir.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
          <Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
 Bu örnekte XML [alt eksen özelliği](../../../language-reference/xml-axis/xml-child-axis-property.md), [XML özniteliği eksen özelliği](../../../language-reference/xml-axis/xml-attribute-axis-property.md)ve [XML değeri özelliği](../../../language-reference/xml-axis/xml-value-property.md)kullanılmıştır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Temel sorgular (LINQ to XML) (Visual Basic)](basic-queries-linq-to-xml.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md)
- [Projeksiyon Işlemleri (Visual Basic)](projection-operations.md)
