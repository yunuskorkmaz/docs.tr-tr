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
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="9229f-102">Nasıl yapılır: yeni bir tür proje (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9229f-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="9229f-103">Bu bölümdeki diğer örneklerde, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, `string`<xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.Generic.IEnumerable%601> `int`olarak sonuçlar döndüren sorgular gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9229f-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="9229f-104">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="9229f-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="9229f-105">Çoğu durumda, sorgularınızın başka türden bir <xref:System.Collections.Generic.IEnumerable%601> döndürmesini isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9229f-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9229f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9229f-106">Example</span></span>  
 <span data-ttu-id="9229f-107">Bu örnek, `Select` yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9229f-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="9229f-108">Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `Select` deyimini değiştirerek ifade yeni sınıfın yeni bir örneği olur.</span><span class="sxs-lookup"><span data-stu-id="9229f-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="9229f-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9229f-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9229f-110">Bu örnekte, [nasıl yapılır: tek alt öğe alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda açıklanan `M:System.Xml.Linq.XElement.Element` yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9229f-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="9229f-111">Ayrıca, `M:System.Xml.Linq.XElement.Element` yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9229f-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="9229f-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9229f-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="9229f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9229f-113">See also</span></span>

- [<span data-ttu-id="9229f-114">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9229f-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
