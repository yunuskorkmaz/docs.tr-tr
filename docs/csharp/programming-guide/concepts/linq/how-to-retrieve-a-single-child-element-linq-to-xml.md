---
title: Tek bir alt öğe alma (LINQ to XML) (C#)
description: Tek bir alt öğeyi ada göre almak için LINQ to XML nasıl kullanacağınızı öğrenin. Bu C# örneğinde, öğe yöntemi belirtilen ilk alt öğeyi döndürür.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103283"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Tek bir alt öğe alma (LINQ to XML) (C#)
Bu konu, alt öğenin adı verildiğinde tek bir alt öğenin nasıl alınacağını açıklar. Alt öğenin adını bildiğiniz ve bu ada sahip yalnızca bir öğe olduğunda, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A>Yöntemi, belirtilen ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> .  
  
 Visual Basic tek bir alt öğe almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanmak ve sonra dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yönteminin kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> . Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğeyi bulur `Comment` .  
  
 Visual Basic örnek, tek bir öğeyi almak için dizi dizin oluşturucu gösterimini kullanmayı gösterir.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı kodu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
