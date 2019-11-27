---
title: 'Nasıl yapılır: yeni bir tür proje (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: a2486d88af537fb4aa8f34243a5a739d25ee5be1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353330"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Nasıl yapılır: yeni bir tür proje (LINQ to XML) (Visual Basic)
Bu bölümdeki diğer örneklerde, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, `string`<xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.Generic.IEnumerable%601> `int`olarak sonuçlar döndüren sorgular gösterilmiştir. Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka türden bir <xref:System.Collections.Generic.IEnumerable%601> döndürmesini isteyeceksiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir. Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `Select` deyimini değiştirerek ifade yeni sınıfın yeni bir örneği olur.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Bu örnekte, [nasıl yapılır: tek alt öğe alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda açıklanan `M:System.Xml.Linq.XElement.Element` yöntemi kullanılmaktadır. Ayrıca, `M:System.Xml.Linq.XElement.Element` yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır.  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
