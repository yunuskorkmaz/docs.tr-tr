---
title: 'Nasıl yapılır: Ara Değerleri Hesaplama'
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: bc38d4848a26a24aeb00581079c9dd31abb7ba1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375102"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="208ff-102">Nasıl yapılır: ara değerleri hesaplama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="208ff-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="208ff-103">Bu örnek, sıralama, filtreleme ve seçme için kullanılabilen ara değerlerin nasıl hesaplanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="208ff-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="208ff-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="208ff-104">Example</span></span>  
 <span data-ttu-id="208ff-105">Aşağıdaki örnek `Let` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="208ff-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="208ff-106">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="208ff-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="208ff-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="208ff-107">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="208ff-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="208ff-108">Example</span></span>  
 <span data-ttu-id="208ff-109">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="208ff-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="208ff-110">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="208ff-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="208ff-111">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında sayısal veri](sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="208ff-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="208ff-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="208ff-112">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="208ff-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="208ff-113">See also</span></span>

- [<span data-ttu-id="208ff-114">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="208ff-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
