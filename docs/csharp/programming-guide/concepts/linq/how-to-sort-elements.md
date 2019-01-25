---
title: 'Nasıl yapılır: Öğeleri sıralama (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 66a41fc018b2df64aa95c24d1d698b6c38fd189a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640790"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="222fc-102">Nasıl yapılır: Öğeleri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="222fc-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="222fc-103">Bu örnek, sonuçları sıralayan sorgu yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="222fc-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="222fc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="222fc-104">Example</span></span>  
 <span data-ttu-id="222fc-105">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="222fc-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="222fc-106">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222fc-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="222fc-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="222fc-107">Example</span></span>  
 <span data-ttu-id="222fc-108">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="222fc-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="222fc-109">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="222fc-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="222fc-110">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace alanında sayısal veriler](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="222fc-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="222fc-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222fc-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="222fc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="222fc-112">See also</span></span>

- [<span data-ttu-id="222fc-113">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="222fc-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="222fc-114">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="222fc-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
