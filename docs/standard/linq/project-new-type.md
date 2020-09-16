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
# <a name="how-to-project-a-new-type-linq-to-xml"></a>Yeni bir türü yansıtma (LINQ to XML)

Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ,, ve ' den itibaren sonuç döndüren sorgular gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> `int` . Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın <xref:System.Collections.Generic.IEnumerable%601> başka bir türden birini döndürmesini isteyeceksiniz.

## <a name="example-define-a-new-type-and-have-the-select-statement-create-an-instance-of-the-type"></a>Örnek: yeni bir tür tanımlayın ve `select` deyimin türün bir örneğini oluşturmasını sağlayabilirsiniz

Bu örnek, yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir `select` . Kod, ilk olarak yeni bir sınıf tanımlamak için bir oluşturucu çağırır ve sonra deyimi, `select` ifadenin yeni bir örneği olacak şekilde değiştirir. Örnek, XML belgesi [örnek xml dosyasını kullanır: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).

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

Bu örnek <xref:System.Xml.Linq.XContainer.Element%2A> , [tek bir alt öğe alma](retrieve-single-child-element.md) makalesinde tanıtılan yöntemi kullanır. Ayrıca, yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır <xref:System.Xml.Linq.XContainer.Element%2A> .

Bu örnek aşağıdaki çıktıyı üretir:

```output
Lawnmower:1
Baby Monitor:2
```

## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](./work-dictionaries-linq-xml.md)
