---
title: 'Nasıl yapılır: öğeleri (C#) sıralama'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7548f183736ac9ed0ed09d3be775b3ffde6cb255
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552554"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="03b2a-102">Nasıl yapılır: öğeleri (C#) sıralama</span><span class="sxs-lookup"><span data-stu-id="03b2a-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="03b2a-103">Bu örnek, sonuçları sıralayan sorgu yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="03b2a-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03b2a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="03b2a-104">Example</span></span>  
 <span data-ttu-id="03b2a-105">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="03b2a-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="03b2a-106">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="03b2a-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="03b2a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="03b2a-107">Example</span></span>  
 <span data-ttu-id="03b2a-108">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="03b2a-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="03b2a-109">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="03b2a-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="03b2a-110">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal verilerinde bir Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="03b2a-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="03b2a-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="03b2a-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="03b2a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03b2a-112">See Also</span></span>

- [<span data-ttu-id="03b2a-113">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="03b2a-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
- [<span data-ttu-id="03b2a-114">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="03b2a-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
