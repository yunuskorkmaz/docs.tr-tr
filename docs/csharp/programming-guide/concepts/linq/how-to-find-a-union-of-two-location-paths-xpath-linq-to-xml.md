---
title: 'Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: ebb2ddc3a7ba5e08e99cecca01294e5ad3182e8b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253854"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="544d1-102">Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="544d1-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="544d1-103">XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="544d1-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="544d1-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="544d1-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="544d1-105"><xref:System.Linq.Enumerable.Concat%2A> Standart sorgu işlecini kullanarak aynı sonuçları elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="544d1-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="544d1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="544d1-106">Example</span></span>  
 <span data-ttu-id="544d1-107">Bu örnek tüm `Category` öğeleri ve tüm `Price` öğeleri bulur ve bunları tek bir koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="544d1-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="544d1-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Sorgunun sonuçları sıralamak için çağrı <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> yaptığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="544d1-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="544d1-109">XPath ifadesi değerlendirmesi sonuçları da belge sırasıyla bulunur.</span><span class="sxs-lookup"><span data-stu-id="544d1-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="544d1-110">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="544d1-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="544d1-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="544d1-111">This example produces the following output:</span></span>  
  
```output  
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
  