---
title: 'Nasıl yapılır: Öğeleri sıralama (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0b338dc67bca38f471f37abf28149e5080a01987
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484902"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="53452-102">Nasıl yapılır: Öğeleri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="53452-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="53452-103">Bu örnek, sonuçları sıralayan sorgu yazma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="53452-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53452-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="53452-104">Example</span></span>  
 <span data-ttu-id="53452-105">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="53452-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="53452-106">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="53452-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="53452-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="53452-107">Example</span></span>  
 <span data-ttu-id="53452-108">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="53452-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="53452-109">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="53452-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="53452-110">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace alanında sayısal veriler](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="53452-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="53452-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="53452-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="53452-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53452-112">See also</span></span>

- [<span data-ttu-id="53452-113">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="53452-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)
