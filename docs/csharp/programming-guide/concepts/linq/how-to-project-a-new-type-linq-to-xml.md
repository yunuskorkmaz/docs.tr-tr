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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Yeni bir tür proje (LINQ to XML) (C#)

Bu bölümdeki diğer örneklerde, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, `string`<xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.Generic.IEnumerable%601> `int`olarak sonuçlar döndüren sorgular gösterilmiştir. Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka türden bir <xref:System.Collections.Generic.IEnumerable%601> döndürmesini isteyeceksiniz.

## <a name="example"></a>Örnek

Bu örnek, `select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir. Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `select` deyimini değiştirerek ifade yeni sınıfın yeni bir örneği olur.

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

Bu örnekte, [tek bir alt öğe alma (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md)konusundaki konu başlığında tanıtılan <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi kullanılmaktadır. Ayrıca, <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır.  

Bu örnek aşağıdaki çıktıyı üretir:

```output
Lawnmower:1
Baby Monitor:2
```
