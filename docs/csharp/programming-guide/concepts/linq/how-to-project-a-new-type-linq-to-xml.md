---
title: Yeni bir tür (LINQ - XML) (C#) nasıl projeyapılır?
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 5205a0c56651271dea0181ed96518c0e9d7f95f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168999"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="72abb-102">Yeni bir tür (LINQ - XML) (C#) nasıl projeyapılır?</span><span class="sxs-lookup"><span data-stu-id="72abb-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="72abb-103">Bu bölümdeki <xref:System.Collections.Generic.IEnumerable%601> diğer <xref:System.Xml.Linq.XElement>örnekler, ' ın ve <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> . `int`</span><span class="sxs-lookup"><span data-stu-id="72abb-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="72abb-104">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="72abb-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="72abb-105">Çoğu durumda, sorgularınızın başka bir <xref:System.Collections.Generic.IEnumerable%601> türde bir döndürmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="72abb-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="72abb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="72abb-106">Example</span></span>

<span data-ttu-id="72abb-107">Bu örnek, `select` yan tümcedeki nesnelerin nasıl anlık olarak anlık olarak nasıl açIlebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="72abb-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="72abb-108">Kod önce bir oluşturucu ile yeni bir sınıf tanımlar `select` ve daha sonra ifade yeni sınıfın yeni bir örnek olacak şekilde deyimi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="72abb-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="72abb-109">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="72abb-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="72abb-110">Bu örnek, <xref:System.Xml.Linq.XContainer.Element%2A> tek [bir alt öğe (LINQ- XML) (C#) nasıl alınır,](how-to-retrieve-a-single-child-element-linq-to-xml.md)konuyla tanıtılan yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="72abb-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="72abb-111">Ayrıca <xref:System.Xml.Linq.XContainer.Element%2A> yöntem tarafından döndürülen öğelerin değerlerini almak için dökümleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="72abb-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="72abb-112">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="72abb-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
