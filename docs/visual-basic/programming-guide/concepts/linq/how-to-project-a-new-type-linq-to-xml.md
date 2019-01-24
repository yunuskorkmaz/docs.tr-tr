---
title: 'Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 5d0679c3c6f1fa26408905799f5b7a5d0cef6266
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592104"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (Visual Basic)
Bu bölümdeki diğer örnekler, sonuç olarak döndüren sorgular gösterilmesini <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> , `string`, ve <xref:System.Collections.Generic.IEnumerable%601> , `int`. Bunlar ortak sonuç türleri, ancak her senaryo için uygun değildir. Çoğu durumda sorgularınızın döndürülecek isteyeceksiniz bir <xref:System.Collections.Generic.IEnumerable%601> başka bir tür.  
  
## <a name="example"></a>Örnek  
 Bu örnek nesneleri oluşturmak nasıl gösterir `Select` yan tümcesi. Kod öncelikle bir oluşturucuya sahip yeni bir sınıf tanımlar ve sonra değiştirir `Select` deyimi deyim yeni sınıfının yeni bir örneğini olmasını sağlayın.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
  
 Bu örnekte `M:System.Xml.Linq.XElement.Element` konu başlığı altında tanıtılan yöntemi [nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Tarafından döndürülen öğe değerlerini almak için atamalar da kullandığı `M:System.Xml.Linq.XElement.Element` yöntemi.  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Projeksiyonlar ve Dönüşümler (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
