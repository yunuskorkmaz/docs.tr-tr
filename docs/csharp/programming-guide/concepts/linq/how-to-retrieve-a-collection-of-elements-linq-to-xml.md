---
title: 'Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 8d2aab59a6c2a72d796bfaf40755bdf280c81b6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320423"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (C#)
Bu konuda gösterilir <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi. Bu yöntem, bir öğenin alt öğelerinin koleksiyonunu alır.  
  
## <a name="example"></a>Örnek  
 Bu örnek alt öğelerini tekrarlanan `purchaseOrder` öğesi.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Bu örnek şu çıkışı üretir.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
