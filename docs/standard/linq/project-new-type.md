---
title: Yeni bir tür proje-LINQ to XML
description: Sorgunuz, yaygın olanlardan farklı türde bir IEnumerable döndürebilir. Bu makalede bir örnek gösterilmektedir.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: a0ce8d9e5199b290dc759c191c4db7a37ddc9a55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547538"
---
# <a name="how-to-project-a-new-type-linq-to-xml"></a><span data-ttu-id="3d101-104">Yeni bir türü yansıtma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3d101-104">How to project a new type (LINQ to XML)</span></span>

<span data-ttu-id="3d101-105">Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ,, ve ' den itibaren sonuç döndüren sorgular gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="3d101-105">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="3d101-106">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="3d101-106">These are common result types, but they're not appropriate for every scenario.</span></span> <span data-ttu-id="3d101-107">Çoğu durumda, sorgularınızın <xref:System.Collections.Generic.IEnumerable%601> başka bir türden birini döndürmesini isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="3d101-107">In many cases, you'll want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a><span data-ttu-id="3d101-108">Örnek: yeni bir tür tanımlayın ve `select` deyimin türün bir örneğini oluşturmasını sağlayabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="3d101-108">Example: Define a new type and have the `select` statement create an instance of the type</span></span>

<span data-ttu-id="3d101-109">Bu örnek, yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir `select` .</span><span class="sxs-lookup"><span data-stu-id="3d101-109">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="3d101-110">Kod, ilk olarak yeni bir sınıf tanımlamak için bir oluşturucu çağırır ve sonra deyimi, `select` ifadenin yeni bir örneği olacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3d101-110">The code first invokes a constructor to define a new class, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span> <span data-ttu-id="3d101-111">Örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="3d101-111">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");

        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );

        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

```vb
Public Class NameQty
    Public name As String
    Public qty As Integer
    Public Sub New(ByVal n As String, ByVal q As Integer)
        name = n
        qty = q
    End Sub
End Class

Public Class Program
    Shared Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")

        Dim nqList As IEnumerable(Of NameQty) = _
            From n In po...<Item> _
            Select New NameQty( _
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))

        For Each n As NameQty In nqList
            Console.WriteLine(n.name & ":" & n.qty)
        Next
    End Sub
End Class
```

<span data-ttu-id="3d101-112">Bu örnek <xref:System.Xml.Linq.XContainer.Element%2A> , [tek bir alt öğe alma](retrieve-single-child-element.md) makalesinde tanıtılan yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3d101-112">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the [How to retrieve a single child element](retrieve-single-child-element.md) article.</span></span> <span data-ttu-id="3d101-113">Ayrıca, yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="3d101-113">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>

<span data-ttu-id="3d101-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d101-114">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a><span data-ttu-id="3d101-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d101-115">See also</span></span>

- [<span data-ttu-id="3d101-116">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d101-116">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](./work-dictionaries-linq-xml.md)
