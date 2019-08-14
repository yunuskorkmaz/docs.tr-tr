---
title: 'Nasıl yapılır: Yeni bir tür projesi (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 2bb521d1445dcecdad8b9c7b28bed90e1e38c8e8
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012922"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Nasıl yapılır: Yeni bir tür projesi (LINQ to XML) (C#)

Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerable%601> `string` ,,<xref:System.Collections.Generic.IEnumerable%601> ve ' den itibaren sonuç`int`döndürensorgulargösterilmiştir. <xref:System.Xml.Linq.XElement> Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka bir <xref:System.Collections.Generic.IEnumerable%601> türden birini döndürmesini isteyeceksiniz.

## <a name="example"></a>Örnek

Bu örnek, `select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir. Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `select` deyimi, ifadenin yeni bir sınıf örneği olacak şekilde değiştirir.

Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).

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

Bu örnekte, konusunda <xref:System.Xml.Linq.XContainer.Element%2A> açıklanan yöntemi [kullanılmıştır: Tek bir alt öğe al (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Ayrıca, <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır.  

Bu örnek aşağıdaki çıktıyı üretir:

```console
Lawnmower:1
Baby Monitor:2
```
