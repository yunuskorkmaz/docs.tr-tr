---
title: 'Nasıl yapılır: Ara değerleri hesapla (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fe3f992e85b3fb508fced943e1428a4fb6ae2490
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205375"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="a81ab-102">Nasıl yapılır: Ara değerleri hesapla (C#)</span><span class="sxs-lookup"><span data-stu-id="a81ab-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="a81ab-103">Bu örnek, sıralama, filtreleme ve seçme için kullanılabilen ara değerlerin nasıl hesaplanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a81ab-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81ab-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a81ab-104">Example</span></span>  
 <span data-ttu-id="a81ab-105">Aşağıdaki örnek `Let` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a81ab-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="a81ab-106">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a81ab-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="a81ab-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a81ab-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="a81ab-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a81ab-108">Example</span></span>  
 <span data-ttu-id="a81ab-109">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a81ab-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a81ab-110">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a81ab-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a81ab-111">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanındaki](./sample-xml-file-numerical-data-in-a-namespace.md)sayısal veri.</span><span class="sxs-lookup"><span data-stu-id="a81ab-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="a81ab-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a81ab-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
