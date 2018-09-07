---
title: 'Nasıl yapılır: ara değerleri (C#) hesaplama'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 15ccf58738b64ebfaef77deb162ddb29db0ae33a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071037"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="4a5f2-102">Nasıl yapılır: ara değerleri (C#) hesaplama</span><span class="sxs-lookup"><span data-stu-id="4a5f2-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="4a5f2-103">Bu örnek, sıralama, filtreleme ve seçme içinde kullanılan ara değerleri hesaplama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4a5f2-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a5f2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a5f2-104">Example</span></span>  
 <span data-ttu-id="4a5f2-105">Aşağıdaki örnekte `Let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4a5f2-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="4a5f2-106">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4a5f2-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4a5f2-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4a5f2-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="4a5f2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a5f2-108">Example</span></span>  
 <span data-ttu-id="4a5f2-109">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a5f2-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4a5f2-110">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4a5f2-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="4a5f2-111">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: sayısal verilerinde bir Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4a5f2-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="4a5f2-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4a5f2-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a5f2-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a5f2-113">See Also</span></span>

- [<span data-ttu-id="4a5f2-114">Temel sorgular (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4a5f2-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
