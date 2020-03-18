---
title: Bir alt öğe (XPath-LINQ - XML) (C#) nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 37ce6c9d91d4edf2576ccddabd1d7f14a96b0a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141244"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a>Bir alt öğe (XPath-LINQ - XML) (C#) nasıl bulabilirim?
Bu konu, XPath alt öğesi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> eksenini yöntemle karşılaştırır.  
  
 XPath ifadesi `DeliveryNotes`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte alt `DeliveryNotes`öğeyi bulur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Birden Çok SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  