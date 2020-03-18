---
title: Tek bir alt öğe (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347470"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Tek bir alt öğe (LINQ - XML) (C#) nasıl alınır?
Bu konu, alt öğenin adı verilen tek bir alt öğenin nasıl alınır açıklar. Alt öğenin adını biliyorsanız ve bu ada sahip tek bir öğe varsa, koleksiyon yerine yalnızca bir öğeyi almak uygun olabilir.  
  
 Yöntem <xref:System.Xml.Linq.XContainer.Element%2A> belirtilen ile <xref:System.Xml.Linq.XElement> ilk alt <xref:System.Xml.Linq.XName>döndürür.  
  
 Visual Basic'te tek bir alt öğe almak istiyorsanız, sık karşılaşılan bir yaklaşım XML özelliğini kullanmak ve ardından dizi dizileyici gösterimini kullanarak ilk öğeyi almaktır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yöntemin <xref:System.Xml.Linq.XContainer.Element%2A> kullanımını göstermektedir. Bu örnek, XML `po` ağacı adlı alır `Comment`ve adlı ilk öğeyi bulur.  
  
 Visual Basic örneği, tek bir öğeyi almak için dizi dizinleyici gösterimini kullanırken gösterir.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, xml için bir ad alanında aynı kodu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Tipik Satın Alma Siparişi.](./sample-xml-file-typical-purchase-order-in-a-namespace.md)  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)
