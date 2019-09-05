---
title: 'Nasıl yapılır: Öğeleri Sırala (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: e5f76518437954ac683ec2e3e30ad9007c280f83
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253307"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="6b69f-102">Nasıl yapılır: Öğeleri Sırala (C#)</span><span class="sxs-lookup"><span data-stu-id="6b69f-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="6b69f-103">Bu örnek, sonuçlarını sıralayan bir sorgunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b69f-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b69f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b69f-104">Example</span></span>  
 <span data-ttu-id="6b69f-105">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6b69f-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6b69f-106">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6b69f-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="6b69f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b69f-107">Example</span></span>  
 <span data-ttu-id="6b69f-108">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b69f-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6b69f-109">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6b69f-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="6b69f-110">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanındaki](./sample-xml-file-numerical-data-in-a-namespace.md)sayısal veri.</span><span class="sxs-lookup"><span data-stu-id="6b69f-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="6b69f-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6b69f-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b69f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b69f-112">See also</span></span>

- [<span data-ttu-id="6b69f-113">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="6b69f-113">Sorting Data (C#)</span></span>](./sorting-data.md)
