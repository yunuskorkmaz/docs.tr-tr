---
title: 'Nasıl yapılır: iki konum yolları (XPath-LINQ-XML) birleşimini Bul (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: cd98c1da2f2f8653c5db36f89a63dfdc7a7ab691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333303"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="80b1d-102">Nasıl yapılır: iki konum yolları (XPath-LINQ-XML) birleşimini Bul (C#)</span><span class="sxs-lookup"><span data-stu-id="80b1d-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="80b1d-103">XPath iki XPath Konum yolları sonuçlarını birleşimi bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="80b1d-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="80b1d-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="80b1d-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="80b1d-105">Kullanarak aynı sonucu elde edebilirsiniz <xref:System.Linq.Enumerable.Concat%2A> standart sorgu işleci.</span><span class="sxs-lookup"><span data-stu-id="80b1d-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80b1d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="80b1d-106">Example</span></span>  
 <span data-ttu-id="80b1d-107">Bu örnekte tüm bulur `Category` öğeleri ve tüm `Price` öğeleri ve bunları tek bir koleksiyona art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="80b1d-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="80b1d-108">Unutmayın [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu çağrıları <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sonuçları sıralamak için.</span><span class="sxs-lookup"><span data-stu-id="80b1d-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="80b1d-109">XPath ifadesi değerlendirme sonuçlarını da belge sıradadır.</span><span class="sxs-lookup"><span data-stu-id="80b1d-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="80b1d-110">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: sayısal verileri (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="80b1d-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="80b1d-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="80b1d-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80b1d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80b1d-112">See Also</span></span>  
 [<span data-ttu-id="80b1d-113">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="80b1d-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
