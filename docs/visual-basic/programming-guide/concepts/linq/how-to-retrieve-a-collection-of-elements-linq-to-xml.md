---
title: 'Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 7ebc33ec8d1901ecb795f63b2fd9812d1acba347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640176"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="d45e4-102">Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d45e4-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d45e4-103">Bu konuda gösterilir <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d45e4-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="d45e4-104">Bu yöntem, bir öğenin alt öğelerinin koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="d45e4-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d45e4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d45e4-105">Example</span></span>  
 <span data-ttu-id="d45e4-106">Bu örnek alt öğelerini tekrarlanan `purchaseOrder` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d45e4-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="d45e4-107">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d45e4-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="d45e4-108">Bu örnek şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="d45e4-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="d45e4-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d45e4-109">See Also</span></span>  
 [<span data-ttu-id="d45e4-110">LINQ-XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d45e4-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
