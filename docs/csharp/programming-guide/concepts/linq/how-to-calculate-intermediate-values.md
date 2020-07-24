---
title: Ara değerleri hesaplama (C#)
description: C# ' deki bu LINQ to XML örneği sıralama, filtreleme ve seçme için kullanılabilen ara değerlerin nasıl hesaplanacağını gösterir.
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103618"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="a8f74-103">Ara değerleri hesaplama (C#)</span><span class="sxs-lookup"><span data-stu-id="a8f74-103">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="a8f74-104">Bu örnek, sıralama, filtreleme ve seçme için kullanılabilen ara değerlerin nasıl hesaplanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8f74-104">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8f74-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8f74-105">Example</span></span>  
 <span data-ttu-id="a8f74-106">Aşağıdaki örnek `Let` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8f74-106">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="a8f74-107">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a8f74-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a8f74-108">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a8f74-108">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="a8f74-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8f74-109">Example</span></span>  
 <span data-ttu-id="a8f74-110">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8f74-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a8f74-111">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a8f74-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a8f74-112">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında sayısal veri](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="a8f74-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="a8f74-113">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="a8f74-113">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
