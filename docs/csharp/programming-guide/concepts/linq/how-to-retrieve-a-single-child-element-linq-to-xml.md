---
title: "Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 722a6b6630fd08a328a26dcef4d72a8cdd817924
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="447b0-102">Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (C#)</span><span class="sxs-lookup"><span data-stu-id="447b0-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="447b0-103">Bu konuda, tek bir alt öğe, alt öğe adı verilen almak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="447b0-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="447b0-104">Adı alt öğe ve bu ada sahip olan yalnızca bir öğe olduğunu bildiğiniz durumlarda bir koleksiyon yerine yalnızca tek bir öğede almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="447b0-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="447b0-105"><xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> belirtilen <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="447b0-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="447b0-106">Tek bir alt öğe Visual Basic'te almak istiyorsanız, bir ortak XML özelliğini kullanın ve ardından dizinin dizin oluşturucu gösterimini kullanarak ilk öğe almak için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="447b0-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="447b0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="447b0-107">Example</span></span>  
 <span data-ttu-id="447b0-108">Aşağıdaki örnek kullanımını gösteren <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="447b0-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="447b0-109">Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğe bulur `Comment`.</span><span class="sxs-lookup"><span data-stu-id="447b0-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="447b0-110">Visual Basic örnek, tek bir öğe almak için dizi dizin oluşturucu gösterimini kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="447b0-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="447b0-111">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="447b0-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="447b0-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="447b0-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="447b0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="447b0-113">Example</span></span>  
 <span data-ttu-id="447b0-114">Aşağıdaki örnek, bir ad alanı içinde XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="447b0-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="447b0-115">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="447b0-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="447b0-116">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace tipik satınalma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="447b0-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="447b0-117">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="447b0-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="447b0-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="447b0-118">See Also</span></span>  
 [<span data-ttu-id="447b0-119">LINQ-XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="447b0-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
