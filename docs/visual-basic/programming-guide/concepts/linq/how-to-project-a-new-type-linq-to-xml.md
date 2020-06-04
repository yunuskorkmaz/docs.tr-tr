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
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="e2c99-102">Nasıl yapılır: yeni bir tür proje (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c99-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e2c99-103">Bu bölümdeki diğer örneklerde <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ,, ve ' den itibaren sonuç döndüren sorgular gösterilmiştir <xref:System.Collections.Generic.IEnumerable%601> `string` <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="e2c99-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="e2c99-104">Bunlar yaygın sonuç türleridir, ancak her senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="e2c99-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="e2c99-105">Çoğu durumda, sorgularınızın başka bir türden birini döndürmesini isteyeceksiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="e2c99-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2c99-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2c99-106">Example</span></span>  
 <span data-ttu-id="e2c99-107">Bu örnek, yan tümcesindeki nesnelerin örneğini oluşturmayı gösterir `Select` .</span><span class="sxs-lookup"><span data-stu-id="e2c99-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="e2c99-108">Kod ilk olarak bir Oluşturucu içeren yeni bir sınıf tanımlar ve ardından `Select` deyimi, ifadenin yeni bir sınıf örneği olacak şekilde değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e2c99-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="e2c99-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e2c99-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e2c99-110">Bu örnek `M:System.Xml.Linq.XElement.Element` , [nasıl yapılır: tek alt öğe alma (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md)konusunda tanıtılan yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2c99-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="e2c99-111">Ayrıca, yöntemi tarafından döndürülen öğelerin değerlerini almak için yayınları kullanır `M:System.Xml.Linq.XElement.Element` .</span><span class="sxs-lookup"><span data-stu-id="e2c99-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="e2c99-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e2c99-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2c99-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2c99-113">See also</span></span>

- [<span data-ttu-id="e2c99-114">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c99-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
