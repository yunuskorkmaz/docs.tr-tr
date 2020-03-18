---
title: Ara değerler nasıl hesaplanır (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141441"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="d980d-102">Ara değerler nasıl hesaplanır (C#)</span><span class="sxs-lookup"><span data-stu-id="d980d-102">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="d980d-103">Bu örnek, sıralama, filtreleme ve seçmede kullanılabilecek ara değerlerin nasıl hesaplanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d980d-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d980d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d980d-104">Example</span></span>  
 <span data-ttu-id="d980d-105">Aşağıdaki örnekte `Let` yan tümce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d980d-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="d980d-106">Bu örnekte aşağıdaki XML belgesi kullanılır: [Örnek XML Dosyası: Sayısal Veriler (LINQ-XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d980d-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="d980d-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d980d-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="d980d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d980d-108">Example</span></span>  
 <span data-ttu-id="d980d-109">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d980d-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d980d-110">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d980d-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d980d-111">Bu örnekte aşağıdaki XML belgesi kullanılır: [Örnek XML Dosyası: Ad alanında Sayısal Veriler.](./sample-xml-file-numerical-data-in-a-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="d980d-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="d980d-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d980d-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
