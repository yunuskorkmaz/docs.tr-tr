---
title: 'Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: a94180705674c8aee3ce45607f89fdbba1c873b7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834666"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="a0977-102">Nasıl yapılır: Yeni bir tür (LINQ to XML) proje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0977-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a0977-103">Bu bölümdeki diğer örnekler, sonuç olarak döndüren sorgular gösterilmesini <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> , `string`, ve <xref:System.Collections.Generic.IEnumerable%601> , `int`.</span><span class="sxs-lookup"><span data-stu-id="a0977-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="a0977-104">Bunlar ortak sonuç türleri, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="a0977-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="a0977-105">Çoğu durumda sorgularınızın döndürülecek isteyeceksiniz bir <xref:System.Collections.Generic.IEnumerable%601> başka bir tür.</span><span class="sxs-lookup"><span data-stu-id="a0977-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0977-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0977-106">Example</span></span>  
 <span data-ttu-id="a0977-107">Bu örnek nesneleri oluşturmak nasıl gösterir `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a0977-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="a0977-108">Kod öncelikle bir oluşturucuya sahip yeni bir sınıf tanımlar ve sonra değiştirir `Select` deyimi deyim yeni sınıfının yeni bir örneğini olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a0977-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="a0977-109">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a0977-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a0977-110">Bu örnekte `M:System.Xml.Linq.XElement.Element` konu başlığı altında tanıtılan yöntemi [nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a0977-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="a0977-111">Tarafından döndürülen öğe değerlerini almak için atamalar da kullandığı `M:System.Xml.Linq.XElement.Element` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a0977-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="a0977-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a0977-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0977-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0977-113">See also</span></span>

- [<span data-ttu-id="a0977-114">Projeksiyonlar ve Dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0977-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
