---
title: Yeni bir tür proje (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 3a54677fa0fa2845dd635f89ddb7ed1c5c279e03
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345715"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="7bf26-102">Yeni bir tür proje (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7bf26-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="7bf26-103">Bu bölümdeki diğer örneklerde, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, `string`<xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.Generic.IEnumerable%601> `int`olarak sonuçlar döndüren sorgular gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7bf26-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="7bf26-104">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="7bf26-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="7bf26-105">Çoğu durumda, sorgularınızın başka türden bir <xref:System.Collections.Generic.IEnumerable%601> döndürmesini isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7bf26-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="7bf26-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bf26-106">Example</span></span>

<span data-ttu-id="7bf26-107">Bu örnek, `select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bf26-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="7bf26-108">Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `select` deyimini değiştirerek ifade yeni sınıfın yeni bir örneği olur.</span><span class="sxs-lookup"><span data-stu-id="7bf26-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="7bf26-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="7bf26-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="7bf26-110">Bu örnekte, [tek bir alt öğe alma (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md)konusundaki konu başlığında tanıtılan <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bf26-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="7bf26-111">Ayrıca, <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7bf26-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="7bf26-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7bf26-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
