---
title: 'Nasıl yapılır: Yeni bir tür projesi (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: bec4e7c7d87dffb90b49b76aa00a5de093d68436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593041"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="ef132-102">Nasıl yapılır: Yeni bir tür projesi (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef132-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="ef132-103">Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerable%601> `string` ,,<xref:System.Collections.Generic.IEnumerable%601> ve ' den itibaren sonuç`int`döndürensorgulargösterilmiştir. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="ef132-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="ef132-104">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="ef132-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="ef132-105">Çoğu durumda, sorgularınızın başka bir <xref:System.Collections.Generic.IEnumerable%601> türden birini döndürmesini isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ef132-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="ef132-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef132-106">Example</span></span>

<span data-ttu-id="ef132-107">Bu örnek, `select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef132-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="ef132-108">Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `select` deyimi, ifadenin yeni bir sınıf örneği olacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ef132-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="ef132-109">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).</span><span class="sxs-lookup"><span data-stu-id="ef132-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="ef132-110">Bu örnekte, konusunda <xref:System.Xml.Linq.XContainer.Element%2A> açıklanan yöntemi [kullanılmıştır: Tek bir alt öğe al (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ef132-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="ef132-111">Ayrıca, <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef132-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="ef132-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef132-112">This example produces the following output:</span></span>

```console
Lawnmower:1
Baby Monitor:2
```
