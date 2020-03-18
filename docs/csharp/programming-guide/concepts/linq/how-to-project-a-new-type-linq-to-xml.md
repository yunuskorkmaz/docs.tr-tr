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
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Yeni bir tür (LINQ - XML) (C#) nasıl projeyapılır?

Bu bölümdeki <xref:System.Collections.Generic.IEnumerable%601> diğer <xref:System.Xml.Linq.XElement>örnekler, ' ın ve <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> . `int` Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka bir <xref:System.Collections.Generic.IEnumerable%601> türde bir döndürmesini istersiniz.

## <a name="example"></a>Örnek

Bu örnek, `select` yan tümcedeki nesnelerin nasıl anlık olarak anlık olarak nasıl açIlebildiğini gösterir. Kod önce bir oluşturucu ile yeni bir sınıf tanımlar `select` ve daha sonra ifade yeni sınıfın yeni bir örnek olacak şekilde deyimi değiştirir.

Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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

Bu örnek, <xref:System.Xml.Linq.XContainer.Element%2A> tek [bir alt öğe (LINQ- XML) (C#) nasıl alınır,](how-to-retrieve-a-single-child-element-linq-to-xml.md)konuyla tanıtılan yöntemi kullanır. Ayrıca <xref:System.Xml.Linq.XContainer.Element%2A> yöntem tarafından döndürülen öğelerin değerlerini almak için dökümleri kullanır.  

Bu örnek, aşağıdaki çıktıyı üretir:

```output
Lawnmower:1
Baby Monitor:2
```
