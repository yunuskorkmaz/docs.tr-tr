---
title: 'Nasıl yapılır: Yeni Bir Tür Yansıtma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 48fb82e870a4fc4fa16cfb48a127f364e6d81f13
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396512"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Nasıl yapılır: yeni bir tür proje (LINQ to XML) (Visual Basic)
Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ,, ve ' den itibaren sonuç döndüren sorgular gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> `int` . Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir. Çoğu durumda, sorgularınızın başka bir türden birini döndürmesini isteyeceksiniz <xref:System.Collections.Generic.IEnumerable%601> .  
  
## <a name="example"></a>Örnek  
 Bu örnek, yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir `Select` . Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `Select` deyimi, ifadenin yeni bir sınıf örneği olacak şekilde değiştirir.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Bu örnek `M:System.Xml.Linq.XElement.Element` , [nasıl yapılır: tek alt öğe alma (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda tanıtılan yöntemi kullanır. Ayrıca, yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır `M:System.Xml.Linq.XElement.Element` .  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
