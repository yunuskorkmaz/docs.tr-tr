---
title: 'Nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: e3b8c9d90f494330b30fe1b35a7fe64f882cae95
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818988"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="07542-102">Nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07542-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="07542-103">Bu konu nasıl tek bir alt öğe, alt öğenin adı verilir alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="07542-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="07542-104">Adı alt öğesi ve bu ada sahip yalnızca bir öğe olduğunu bildiğinizde, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="07542-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="07542-105"><xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi döndürür ilk alt <xref:System.Xml.Linq.XElement> belirtilen <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="07542-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="07542-106">Tek bir alt öğe Visual Basic'te almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanın ve ardından dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi almak oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="07542-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07542-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="07542-107">Example</span></span>  
 <span data-ttu-id="07542-108">Aşağıdaki örnek, kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07542-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="07542-109">Bu örnek adlı XML ağacı alır `po` ve adlı ilk öğeyi bulan `Comment`.</span><span class="sxs-lookup"><span data-stu-id="07542-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="07542-110">Visual Basic örneği, tek bir öğe almak için dizi dizin oluşturucu gösterimini kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="07542-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="07542-111">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="07542-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="07542-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="07542-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="07542-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="07542-113">Example</span></span>  
 <span data-ttu-id="07542-114">Aşağıdaki örnek, bir ad alanındaki XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="07542-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="07542-115">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="07542-115">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="07542-116">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace, tipik satın alma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="07542-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="07542-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="07542-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07542-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07542-118">See also</span></span>

- [<span data-ttu-id="07542-119">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07542-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
