---
title: 'Nasıl yapılır: karmaşık filtrelemeye sahip sorgu yazma'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 28e84b7785948e9d50c08438494b89c906ab8505
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344451"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="9f129-102">Nasıl yapılır: karmaşık filtrelemeye sahip sorgular yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f129-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="9f129-103">Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f129-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="9f129-104">Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9f129-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="9f129-105">Bu konu, karmaşık filtrelemeye sahip sorgu yazma örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f129-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f129-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f129-106">Example</span></span>  
 <span data-ttu-id="9f129-107">Bu örnek, bir `Type` özniteliği "Shipping" ve bir alt `State` öğesi "NY" değerine eşit olan bir alt `Address` öğesi olan tüm `PurchaseOrder` öğelerinin nasıl bulunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f129-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="9f129-108">`Where` yan tümcesinde iç içe geçmiş bir sorgu kullanır ve koleksiyonda herhangi bir öğe varsa `Any` işleci `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f129-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="9f129-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9f129-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9f129-110">`Any` işleci hakkında daha fazla bilgi için bkz. [nicelik işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9f129-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="9f129-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9f129-111">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="9f129-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f129-112">Example</span></span>  
 <span data-ttu-id="9f129-113">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f129-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9f129-114">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9f129-114">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9f129-115">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında birden fazla satın alma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9f129-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="9f129-116">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9f129-116">This code produces the following output:</span></span>  
  
```console  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f129-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f129-117">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="9f129-118">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f129-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="9f129-119">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="9f129-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="9f129-120">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="9f129-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="9f129-121">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="9f129-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="9f129-122">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f129-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="9f129-123">Nicelik belirteci Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f129-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
