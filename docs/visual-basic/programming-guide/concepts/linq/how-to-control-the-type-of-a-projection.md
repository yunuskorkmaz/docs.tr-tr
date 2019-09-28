---
title: 'Nasıl yapılır: Projeksiyon türünü denetleme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 8ec53d1f8e0ae4957857d4b71fddd05205dee6b5
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351734"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="3b731-102">Nasıl yapılır: Projeksiyon türünü denetleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b731-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="3b731-103">Projeksiyon, tek bir veri kümesini alma, filtreleme, şeklini değiştirme ve hatta türünü değiştirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="3b731-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="3b731-104">Çoğu sorgu ifadesi tahminleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3b731-104">Most query expressions perform projections.</span></span> <span data-ttu-id="3b731-105">Bu bölümde gösterilen sorgu ifadelerinin çoğu, <xref:System.Collections.Generic.IEnumerable%601> ' ı <xref:System.Xml.Linq.XElement> ' i değerlendirir, ancak başka türden Koleksiyonlar oluşturmak için projeksiyonun türünü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b731-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="3b731-106">Bu konuda bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b731-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b731-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b731-107">Example</span></span>  
 <span data-ttu-id="3b731-108">Aşağıdaki örnek, `Customer` gibi yeni bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b731-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="3b731-109">Sorgu ifadesi daha sonra `Select` yan tümcesinde yeni `Customer` nesneleri örnekleyen.</span><span class="sxs-lookup"><span data-stu-id="3b731-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="3b731-110">Bu, sorgu ifadesinin türünün <xref:System.Collections.Generic.IEnumerable%601> `Customer` olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3b731-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="3b731-111">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML) ](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3b731-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Public Class Customer  
    Private customerIDValue As String  
    Public Property CustomerID() As String  
        Get  
            Return customerIDValue  
        End Get  
        Set(ByVal value As String)  
            customerIDValue = value  
        End Set  
    End Property  
  
    Private companyNameValue As String  
    Public Property CompanyName() As String  
        Get  
            Return companyNameValue  
        End Get  
        Set(ByVal value As String)  
            companyNameValue = value  
        End Set  
    End Property  
  
    Private contactNameValue As String  
    Public Property ContactName() As String  
        Get  
            Return contactNameValue  
        End Get  
        Set(ByVal value As String)  
            contactNameValue = value  
        End Set  
    End Property  
  
    Public Sub New(ByVal customerID As String, _  
                   ByVal companyName As String, _  
                   ByVal contactName As String)  
        CustomerIDValue = customerID  
        CompanyNameValue = companyName  
        ContactNameValue = contactName  
    End Sub  
  
    Public Overrides Function ToString() As String  
        Return String.Format("{0}:{1}:{2}", Me.CustomerID, Me.CompanyName, Me.ContactName)  
    End Function  
End Class  
  
Sub Main()  
    Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
    Dim custList As IEnumerable(Of Customer) = _  
        From el In custOrd.<Customers>.<Customer> _  
        Select New Customer( _  
            el.@<CustomerID>, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value _  
        )  
    For Each cust In custList  
        Console.WriteLine(cust)  
    Next  
End Sub  
```  
  
 <span data-ttu-id="3b731-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3b731-112">This code produces the following output:</span></span>  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b731-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b731-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="3b731-114">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b731-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
