---
title: 'Nasıl yapılır: Bul önceki eşdüzey (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 64c5bc35899f85e107ccc9d6b0bf93eefb5576ef
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753977"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a><span data-ttu-id="a0021-102">Nasıl yapılır: Bul önceki eşdüzey (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0021-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="a0021-103">Bu konu XPath karşılaştırır `preceding-sibling` eksene [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] alt <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> ekseni.</span><span class="sxs-lookup"><span data-stu-id="a0021-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> axis.</span></span>  
  
 <span data-ttu-id="a0021-104">XPath ifadesidir:</span><span class="sxs-lookup"><span data-stu-id="a0021-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="a0021-105">Unutmayın ikisi için de sonuçları <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> ve <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> belge sıradadır.</span><span class="sxs-lookup"><span data-stu-id="a0021-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0021-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0021-106">Example</span></span>  
 <span data-ttu-id="a0021-107">Aşağıdaki örnek bulur `FullAddress` öğesini ve ardından önceki öğeleri kullanarak alır `preceding-sibling` ekseni.</span><span class="sxs-lookup"><span data-stu-id="a0021-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="a0021-108">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="a0021-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="a0021-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a0021-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0021-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0021-110">See Also</span></span>  
 [<span data-ttu-id="a0021-111">LINQ to XML için XPath kullanıcıları (C#)</span><span class="sxs-lookup"><span data-stu-id="a0021-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
