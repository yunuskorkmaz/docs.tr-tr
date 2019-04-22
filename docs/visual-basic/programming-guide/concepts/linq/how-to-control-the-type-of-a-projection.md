---
title: 'Nasıl yapılır: (Visual Basic) projeksiyon türünü denetleme'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: dd09914a75a8d4b20ddf9ff452f046bf7671152f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831411"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a><span data-ttu-id="25d0f-102">Nasıl yapılır: (Visual Basic) projeksiyon türünü denetleme</span><span class="sxs-lookup"><span data-stu-id="25d0f-102">How to: Control the Type of a Projection (Visual Basic)</span></span>
<span data-ttu-id="25d0f-103">Yansıtma, bir veri kümesi alma, filtrelemesini, şeklini değiştirmek ve hatta da türünü değiştirmeyi işlemidir.</span><span class="sxs-lookup"><span data-stu-id="25d0f-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="25d0f-104">Çoğu sorgu ifadeleri tahminler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="25d0f-104">Most query expressions perform projections.</span></span> <span data-ttu-id="25d0f-105">Bu bölümde gösterilen sorgu ifadeleri çoğunu değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, ancak diğer türler oluşturmak için projeksiyon türü denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25d0f-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="25d0f-106">Bu konuda, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25d0f-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d0f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="25d0f-107">Example</span></span>  
 <span data-ttu-id="25d0f-108">Aşağıdaki örnek yeni bir tür tanımlar `Customer`.</span><span class="sxs-lookup"><span data-stu-id="25d0f-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="25d0f-109">Sorgu ifadesi sonra yeni başlatır `Customer` nesneler `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="25d0f-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="25d0f-110">Bu sorgu ifade türünü neden <xref:System.Collections.Generic.IEnumerable%601> , `Customer`.</span><span class="sxs-lookup"><span data-stu-id="25d0f-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="25d0f-111">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="25d0f-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="25d0f-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="25d0f-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="25d0f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25d0f-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="25d0f-114">Projeksiyonlar ve Dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25d0f-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
