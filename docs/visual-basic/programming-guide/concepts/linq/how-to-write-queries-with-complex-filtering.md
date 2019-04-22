---
title: 'Nasıl yapılır: (Visual Basic) karmaşık filtreleme ile sorgu yazma'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: ac58394619b83e2b862e87926f0b6a722fdc3c7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820925"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="b548e-102">Nasıl yapılır: (Visual Basic) karmaşık filtreleme ile sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="b548e-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="b548e-103">Bazen karmaşık filtrelerle XML sorgularında LINQ yazmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b548e-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="b548e-104">Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri Bul gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b548e-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="b548e-105">Bu konu, karmaşık filtreleme ile sorgu yazma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b548e-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b548e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b548e-106">Example</span></span>  
 <span data-ttu-id="b548e-107">Bu örnekte tüm bulmayı gösteren `PurchaseOrder` alt olan öğeler `Address` sahip öğe bir `Type` özniteliği "Gönderim" hem de bir alt gruba eşit `State` öğesi "NY için" eşit.</span><span class="sxs-lookup"><span data-stu-id="b548e-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="b548e-108">İç içe bir sorgu kullanan `Where` yan tümcesi ve `Any` işleci döndürür `True` koleksiyonu herhangi bir öğe varsa.</span><span class="sxs-lookup"><span data-stu-id="b548e-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="b548e-109">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birden fazla satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b548e-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b548e-110">Hakkında daha fazla bilgi için `Any` işleci bkz [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b548e-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="b548e-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b548e-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="b548e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b548e-112">Example</span></span>  
 <span data-ttu-id="b548e-113">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="b548e-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b548e-114">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b548e-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="b548e-115">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace, birden fazla satın alma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b548e-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="b548e-116">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b548e-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="b548e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b548e-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="b548e-118">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b548e-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="b548e-119">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="b548e-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="b548e-120">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="b548e-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="b548e-121">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="b548e-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="b548e-122">Projeksiyon işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b548e-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="b548e-123">Niceleyici işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b548e-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
