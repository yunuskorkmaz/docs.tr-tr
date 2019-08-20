---
title: 'Nasıl yapılır: Tek bir alt öğe al (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 5f2f675f5ce4914124f62981a2591441260b6976
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592622"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Nasıl yapılır: Tek bir alt öğe al (LINQ to XML) (C#)
Bu konu, alt öğenin adı verildiğinde tek bir alt öğenin nasıl alınacağını açıklar. Alt öğenin adını bildiğiniz ve bu ada sahip yalnızca bir öğe olduğunda, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.  
  
 Yöntemi, <xref:System.Xml.Linq.XElement> belirtilen<xref:System.Xml.Linq.XName>ilk alt öğesini döndürür. <xref:System.Xml.Linq.XContainer.Element%2A>  
  
 Visual Basic tek bir alt öğe almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanmak ve sonra dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Xml.Linq.XContainer.Element%2A> yönteminin kullanımını gösterir. Bu örnek adlı `po` xml ağacını alır ve adlı `Comment`ilk öğeyi bulur.  
  
 Visual Basic örnek, tek bir öğeyi almak için dizi dizin oluşturucu gösterimini kullanmayı gösterir.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).  
  
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
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı kodu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanında](./sample-xml-file-typical-purchase-order-in-a-namespace.md)tipik satın alma siparişi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
