---
title: Öğeleri sıralama (C#)
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7fad9fcb43905072c88a5704c56672917bfc377c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347373"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="6193a-102">Öğeleri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="6193a-102">How to sort elements (C#)</span></span>
<span data-ttu-id="6193a-103">Bu örnek, sonuçlarını sıralayan bir sorgunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6193a-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6193a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6193a-104">Example</span></span>  
 <span data-ttu-id="6193a-105">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6193a-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6193a-106">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6193a-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="6193a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6193a-107">Example</span></span>  
 <span data-ttu-id="6193a-108">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6193a-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6193a-109">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6193a-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="6193a-110">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında sayısal veri](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="6193a-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="6193a-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6193a-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="6193a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6193a-112">See also</span></span>

- [<span data-ttu-id="6193a-113">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="6193a-113">Sorting Data (C#)</span></span>](./sorting-data.md)
