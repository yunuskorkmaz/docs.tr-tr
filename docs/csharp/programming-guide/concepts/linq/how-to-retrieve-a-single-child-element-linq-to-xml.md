---
title: 'Nasıl yapılır: tek bir alt öğe (LINQ to XML) alma (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 77ccd56d1d131a740bb90ef4258ef35504f5e3cb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882314"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Nasıl yapılır: tek bir alt öğe (LINQ to XML) alma (C#)
Bu konu nasıl tek bir alt öğe, alt öğenin adı verilir alınacağını açıklar. Adı alt öğesi ve bu ada sahip yalnızca bir öğe olduğunu bildiğinizde, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi döndürür ilk alt <xref:System.Xml.Linq.XElement> belirtilen <xref:System.Xml.Linq.XName>.  
  
 Tek bir alt öğe Visual Basic'te almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanın ve ardından dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi almak oluşturmaktır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi. Bu örnek adlı XML ağacı alır `po` ve adlı ilk öğeyi bulan `Comment`.  
  
 Visual Basic örneği, tek bir öğe almak için dizi dizin oluşturucu gösterimini kullanarak gösterir.  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanındaki XML için aynı kodu gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi bir Namespace,](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
