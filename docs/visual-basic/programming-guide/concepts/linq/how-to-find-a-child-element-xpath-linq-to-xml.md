---
title: 'Nasıl yapılır: bir alt öğesi (XPath-LINQ-XML) bulunamadı (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 122cc269b95a3f35b8eef71e9c7ca1d50af4210b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640464"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="44eb8-102">Nasıl yapılır: bir alt öğesi (XPath-LINQ-XML) bulunamadı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44eb8-102">How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="44eb8-103">Bu konuda XPath alt öğesi eksene karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="44eb8-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="44eb8-104">XPath ifadesi `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="44eb8-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44eb8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="44eb8-105">Example</span></span>  
 <span data-ttu-id="44eb8-106">Bu örnek alt öğesi bulur `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="44eb8-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="44eb8-107">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="44eb8-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="44eb8-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="44eb8-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44eb8-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44eb8-109">See Also</span></span>  
 [<span data-ttu-id="44eb8-110">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44eb8-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
