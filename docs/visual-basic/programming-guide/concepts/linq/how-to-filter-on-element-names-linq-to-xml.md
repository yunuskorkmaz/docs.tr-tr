---
title: 'Nasıl yapılır: Öğe adlarını filtrele (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b1437b4a-48aa-4546-834a-d6d3ab015fe1
ms.openlocfilehash: f64f80b1544e8c5f2d55a44dafe01fee8758d611
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709712"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-visual-basic"></a><span data-ttu-id="029dd-102">Nasıl yapılır: Öğe adlarını filtrele (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="029dd-102">How to: Filter on Element Names (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="029dd-103">' In <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>döndürdüğü yöntemlerden birini çağırdığınızda, öğe adı üzerinde filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="029dd-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="029dd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="029dd-104">Example</span></span>  
 <span data-ttu-id="029dd-105">Bu örnek, yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtrelenen alt öğelerin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="029dd-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="029dd-106">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)).</span><span class="sxs-lookup"><span data-stu-id="029dd-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim items As IEnumerable(Of XElement) = _  
    From el In po...<ProductName> _  
    Select el  
For Each prdName As XElement In items  
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
Next  
```  
  
 <span data-ttu-id="029dd-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="029dd-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="029dd-108">Koleksiyonları<xref:System.Xml.Linq.XElement> döndüren <xref:System.Collections.Generic.IEnumerable%601> diğer yöntemler aynı kalıbı izler.</span><span class="sxs-lookup"><span data-stu-id="029dd-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="029dd-109">İmzaları <xref:System.Xml.Linq.XContainer.Elements%2A> ve ile <xref:System.Xml.Linq.XContainer.Descendants%2A>benzerdir.</span><span class="sxs-lookup"><span data-stu-id="029dd-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="029dd-110">Aşağıda benzer yöntem imzaları olan yöntemlerin tamamı listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="029dd-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="029dd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="029dd-111">Example</span></span>  
 <span data-ttu-id="029dd-112">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="029dd-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="029dd-113">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="029dd-113">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="029dd-114">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanında](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)tipik satın alma siparişi.</span><span class="sxs-lookup"><span data-stu-id="029dd-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim items As IEnumerable(Of XElement) = _  
            From el In po...<aw:ProductName> _  
            Select el  
        For Each prdName As XElement In items  
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="029dd-115">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="029dd-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="029dd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="029dd-116">See also</span></span>

- [<span data-ttu-id="029dd-117">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="029dd-117">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
