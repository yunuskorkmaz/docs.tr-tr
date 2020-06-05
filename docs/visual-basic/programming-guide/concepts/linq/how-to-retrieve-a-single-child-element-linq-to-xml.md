---
title: 'Nasıl yapılır: Tek Bir Alt Öğe Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: ab28ddd960374b22f44ac0c8fc7bddfe0608b8c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397849"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Nasıl yapılır: tek bir alt öğe alma (LINQ to XML) (Visual Basic)
Bu konu, alt öğenin adı verildiğinde tek bir alt öğenin nasıl alınacağını açıklar. Alt öğenin adını bildiğiniz ve bu ada sahip yalnızca bir öğe olduğunda, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A>Yöntemi, belirtilen ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> .  
  
 Visual Basic tek bir alt öğe almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanmak ve sonra dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yönteminin kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> . Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğeyi bulur `Comment` .  
  
 Visual Basic örnek, tek bir öğeyi almak için dizi dizin oluşturucu gösterimini kullanmayı gösterir.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı kodu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](linq-to-xml-axes.md)
