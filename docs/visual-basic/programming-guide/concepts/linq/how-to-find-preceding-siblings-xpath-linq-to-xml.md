---
title: 'Nasıl yapılır: Önceki eşdüzey (XPath-LINQ to XML) bulunamadı (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
ms.openlocfilehash: 4584a84df0e25b451a440c33e17c14cd78fc78bf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833016"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="33d91-102">Nasıl yapılır: Önceki eşdüzey (XPath-LINQ to XML) bulunamadı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d91-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="33d91-103">Bu konu XPath karşılaştırır `preceding-sibling` eksene [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> ekseni.</span><span class="sxs-lookup"><span data-stu-id="33d91-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="33d91-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="33d91-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="33d91-105">Unutmayın ikisi için de sonuçları <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> ve <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> belge sıradadır.</span><span class="sxs-lookup"><span data-stu-id="33d91-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33d91-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="33d91-106">Example</span></span>  
 <span data-ttu-id="33d91-107">Aşağıdaki örnek bulur `FullAddress` öğesini ve ardından önceki öğeleri kullanarak alır `preceding-sibling` ekseni.</span><span class="sxs-lookup"><span data-stu-id="33d91-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="33d91-108">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="33d91-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="33d91-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="33d91-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33d91-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33d91-110">See also</span></span>

- [<span data-ttu-id="33d91-111">LINQ to XML için XPath kullanıcıları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d91-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
