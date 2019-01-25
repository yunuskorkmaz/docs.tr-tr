---
title: 'Nasıl yapılır: Bulma (XPath-LINQ to XML) bir alt öğesi (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 8472a3d9e90aa117c936c4314204f70d2ab33487
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495818"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="83ecb-102">Nasıl yapılır: Bulma (XPath-LINQ to XML) bir alt öğesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83ecb-102">How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="83ecb-103">Bu konu XPath alt öğe eksene karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="83ecb-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="83ecb-104">XPath ifadesi `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="83ecb-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83ecb-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="83ecb-105">Example</span></span>  
 <span data-ttu-id="83ecb-106">Bu örnekte alt öğesi bulur `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="83ecb-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="83ecb-107">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birden fazla satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="83ecb-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="83ecb-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="83ecb-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83ecb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83ecb-109">See also</span></span>
- [<span data-ttu-id="83ecb-110">LINQ to XML için XPath kullanıcıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83ecb-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
