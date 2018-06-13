---
title: 'Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: 9f2b767dcfa68b732eb3f9d0552ec7404658d591
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643251"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="678ce-102">Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ce-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="678ce-103">Bu konuda, tek bir alt öğe, alt öğe adı verilen almak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="678ce-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="678ce-104">Adı alt öğe ve bu ada sahip olan yalnızca bir öğe olduğunu bildiğiniz durumlarda bir koleksiyon yerine yalnızca tek bir öğede almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="678ce-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="678ce-105"><xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> belirtilen <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="678ce-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="678ce-106">Tek bir alt öğe Visual Basic'te almak istiyorsanız, bir ortak XML özelliğini kullanın ve ardından dizinin dizin oluşturucu gösterimini kullanarak ilk öğe almak için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="678ce-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="678ce-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="678ce-107">Example</span></span>  
 <span data-ttu-id="678ce-108">Aşağıdaki örnek kullanımını gösteren <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="678ce-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="678ce-109">Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğe bulur `Comment`.</span><span class="sxs-lookup"><span data-stu-id="678ce-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="678ce-110">Visual Basic örnek, tek bir öğe almak için dizi dizin oluşturucu gösterimini kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="678ce-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="678ce-111">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="678ce-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="678ce-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="678ce-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="678ce-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="678ce-113">Example</span></span>  
 <span data-ttu-id="678ce-114">Aşağıdaki örnek, bir ad alanı içinde XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="678ce-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="678ce-115">Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="678ce-115">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="678ce-116">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace tipik satınalma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="678ce-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="678ce-117">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="678ce-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="678ce-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="678ce-118">See Also</span></span>  
 [<span data-ttu-id="678ce-119">LINQ-XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ce-119">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
