---
title: Yeni bir tür proje (LINQ to XML) (C#)
description: C# ' de LINQ to XML, <T> diğer örneklerde açıklanan XElement, String veya int gibi tür IEnumerable döndüren sorgular oluşturmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104637"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="404af-103">Yeni bir tür proje (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="404af-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="404af-104">Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ,, ve ' den itibaren sonuç döndüren sorgular gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="404af-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="404af-105">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="404af-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="404af-106">Çoğu durumda, sorgularınızın başka bir türden birini döndürmesini isteyeceksiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="404af-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="404af-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="404af-107">Example</span></span>

<span data-ttu-id="404af-108">Bu örnek, yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir `select` .</span><span class="sxs-lookup"><span data-stu-id="404af-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="404af-109">Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `select` deyimi, ifadenin yeni bir sınıf örneği olacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="404af-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="404af-110">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="404af-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="404af-111">Bu örnekte, <xref:System.Xml.Linq.XContainer.Element%2A> [tek bir alt öğe alma (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda açıklanan yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="404af-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="404af-112">Ayrıca, yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="404af-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="404af-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="404af-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
