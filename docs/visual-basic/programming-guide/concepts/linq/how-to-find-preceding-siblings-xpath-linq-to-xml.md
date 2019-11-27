---
title: 'Nasıl yapılır: önceki eşdüzey öğeleri bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
ms.openlocfilehash: be6c546465f659eb633017e47434c86b9f036bf2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344687"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="b7609-102">Nasıl yapılır: önceki eşdüzey öğeleri bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7609-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b7609-103">Bu konu, XPath `preceding-sibling` eksenini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> ekseniyle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b7609-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="b7609-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="b7609-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="b7609-105">Hem <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> hem de <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> sonuçlarının belge sırasıyla olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b7609-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7609-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7609-106">Example</span></span>  
 <span data-ttu-id="b7609-107">Aşağıdaki örnek `FullAddress` öğesini bulur ve sonra `preceding-sibling` eksenini kullanarak önceki öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="b7609-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="b7609-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b7609-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="b7609-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b7609-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7609-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7609-110">See also</span></span>

- [<span data-ttu-id="b7609-111">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7609-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
