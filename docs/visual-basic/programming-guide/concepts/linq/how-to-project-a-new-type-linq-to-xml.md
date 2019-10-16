---
title: 'Nasıl yapılır: yeni bir tür proje (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 64b563c57406caae7869905c417db9e6439e6157
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318364"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Nasıl yapılır: yeni bir tür proje (LINQ to XML) (Visual Basic)
Bu bölümdeki diğer örneklerde, <xref:System.Collections.Generic.IEnumerable%601> ' a <xref:System.Xml.Linq.XElement> ' a, <xref:System.Collections.Generic.IEnumerable%601> `string` ' i ve <xref:System.Collections.Generic.IEnumerable%601> ' ü `int` ' i döndürür. Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka bir türün <xref:System.Collections.Generic.IEnumerable%601> döndürmesini isteyeceksiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek `Select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir. Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `Select` deyimini değiştirerek ifade yeni sınıfın yeni bir örneği olur.  
  
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
  
 Bu örnek, [nasıl yapılır: tek bir alt öğe alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda tanıtılan `M:System.Xml.Linq.XElement.Element` yöntemini kullanır. Ayrıca, `M:System.Xml.Linq.XElement.Element` yöntemiyle döndürülen öğelerin değerlerini almak için yayınları kullanır.  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
