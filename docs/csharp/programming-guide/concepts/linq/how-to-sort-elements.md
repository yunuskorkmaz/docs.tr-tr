---
title: Öğeleri sıralama (C#)
description: Öğeleri sıralamayı öğrenin. Sonuçları bir XML belgesinde sıralayan sorgu yazma örneklerine bakın.
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 669d9cf583e6ab70c93be39ad271eaf104f88718
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301443"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="77250-104">Öğeleri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="77250-104">How to sort elements (C#)</span></span>
<span data-ttu-id="77250-105">Bu örnek, sonuçlarını sıralayan bir sorgunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77250-105">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77250-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="77250-106">Example</span></span>  
 <span data-ttu-id="77250-107">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77250-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="77250-108">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="77250-108">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="77250-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="77250-109">Example</span></span>  
 <span data-ttu-id="77250-110">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="77250-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="77250-111">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="77250-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="77250-112">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında sayısal veri](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="77250-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="77250-113">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="77250-113">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="77250-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77250-114">See also</span></span>

- [<span data-ttu-id="77250-115">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="77250-115">Sorting Data (C#)</span></span>](./sorting-data.md)
