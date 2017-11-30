---
title: "Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3d8cc558191b1ad672660e0d9ada4c4653cd1a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="bd628-102">Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd628-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="bd628-103">Bu konuda gösterilir <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd628-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="bd628-104">Bu yöntem, bir öğenin alt öğelerinin koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="bd628-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd628-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd628-105">Example</span></span>  
 <span data-ttu-id="bd628-106">Bu örnek alt öğelerini tekrarlanan `purchaseOrder` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd628-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="bd628-107">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bd628-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 <span data-ttu-id="bd628-108">Bu örnek şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="bd628-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd628-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd628-109">See Also</span></span>  
 [<span data-ttu-id="bd628-110">LINQ-XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd628-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
