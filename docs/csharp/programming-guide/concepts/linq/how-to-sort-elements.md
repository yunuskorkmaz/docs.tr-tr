---
title: 'Nasıl yapılır: öğeleri (C#) sıralama'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7548f183736ac9ed0ed09d3be775b3ffde6cb255
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042614"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="e018b-102">Nasıl yapılır: öğeleri (C#) sıralama</span><span class="sxs-lookup"><span data-stu-id="e018b-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="e018b-103">Bu örnek, sonuçları sıralayan sorgu yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e018b-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e018b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e018b-104">Example</span></span>  
 <span data-ttu-id="e018b-105">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e018b-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e018b-106">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e018b-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="e018b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e018b-107">Example</span></span>  
 <span data-ttu-id="e018b-108">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="e018b-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e018b-109">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e018b-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="e018b-110">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal verilerinde bir Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="e018b-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e018b-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e018b-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="e018b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e018b-112">See Also</span></span>

- [<span data-ttu-id="e018b-113">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="e018b-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
- [<span data-ttu-id="e018b-114">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e018b-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
