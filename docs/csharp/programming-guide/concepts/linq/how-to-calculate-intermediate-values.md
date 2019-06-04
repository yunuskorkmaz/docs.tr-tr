---
title: 'Nasıl yapılır: Ara değerleri hesaplama (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: cf0300294944d251b739a15edc6ace777eab5bd8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485932"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="73e09-102">Nasıl yapılır: Ara değerleri hesaplama (C#)</span><span class="sxs-lookup"><span data-stu-id="73e09-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="73e09-103">Bu örnek, sıralama, filtreleme ve seçme içinde kullanılan ara değerleri hesaplama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73e09-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73e09-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="73e09-104">Example</span></span>  
 <span data-ttu-id="73e09-105">Aşağıdaki örnekte `Let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="73e09-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="73e09-106">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="73e09-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="73e09-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="73e09-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="73e09-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="73e09-108">Example</span></span>  
 <span data-ttu-id="73e09-109">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="73e09-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="73e09-110">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="73e09-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="73e09-111">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace alanında sayısal veriler](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="73e09-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="73e09-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="73e09-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
