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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Yeni bir tür proje (LINQ to XML) (C#)

Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ,, ve ' den itibaren sonuç döndüren sorgular gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> `int` . Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka bir türden birini döndürmesini isteyeceksiniz <xref:System.Collections.Generic.IEnumerable%601> .

## <a name="example"></a>Örnek

Bu örnek, yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir `select` . Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `select` deyimi, ifadenin yeni bir sınıf örneği olacak şekilde değiştirir.

Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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

Bu örnekte, <xref:System.Xml.Linq.XContainer.Element%2A> [tek bir alt öğe alma (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda açıklanan yöntemi kullanılmaktadır. Ayrıca, yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır <xref:System.Xml.Linq.XContainer.Element%2A> .  

Bu örnek aşağıdaki çıktıyı üretir:

```output
Lawnmower:1
Baby Monitor:2
```
