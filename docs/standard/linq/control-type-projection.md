---
title: Projeksiyonun türünü denetleme-LINQ to XML
description: Sorgunuzun döndürdüğü koleksiyonun türünü kontrol edebilirsiniz; XElements IEnumerable olması gerekmez.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: c4be649a5f35f7e9cbe65332a60b1c8aeb2a66ea
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553533"
---
# <a name="how-to-control-the-type-of-a-projection-linq-to-xml"></a><span data-ttu-id="a793f-103">Projeksiyon türünü denetleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a793f-103">How to control the type of a projection (LINQ to XML)</span></span>

<span data-ttu-id="a793f-104">*Projeksiyon* , bir veri kümesini filtreleme, şeklini ve belki de türünü değiştirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a793f-104">*Projection* is the process of filtering a set of data, changing its shape and perhaps its type.</span></span> <span data-ttu-id="a793f-105">Çoğu sorgu ifadesi projeksiyonlardır.</span><span class="sxs-lookup"><span data-stu-id="a793f-105">Most query expressions do projections.</span></span> <span data-ttu-id="a793f-106">Bu bölümdeki sorgu ifadelerinin çoğu olarak değerlendirilir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , ancak başka türlerde koleksiyonlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a793f-106">Most of the query expressions in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can create collections of other types.</span></span> <span data-ttu-id="a793f-107">Bu makalede bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a793f-107">This article shows how to do this.</span></span>

## <a name="example-define-a-new-type-and-create-a-query-that-creates-an-ienumerable-of-that-type"></a><span data-ttu-id="a793f-108">Örnek: yeni bir tür tanımlayın ve bu türden bir IEnumerable oluşturan bir sorgu oluşturun</span><span class="sxs-lookup"><span data-stu-id="a793f-108">Example: Define a new type and create a query that creates an IEnumerable of that type</span></span>

<span data-ttu-id="a793f-109">Aşağıdaki örnek yeni bir türü tanımlar, `Customer` ve sorgu ifadesi `Customer` yan tümcesindeki yeni nesneleri örnekleyen `Select` .</span><span class="sxs-lookup"><span data-stu-id="a793f-109">The following example defines a new type, `Customer`, and the query expression instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="a793f-110">Bu, sorgu ifadesinin türünün olmasına neden olur <xref:System.Collections.Generic.IEnumerable%601> `Customer` .</span><span class="sxs-lookup"><span data-stu-id="a793f-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span> <span data-ttu-id="a793f-111">Örnek, XML belgesi [örnek xml dosyasını kullanır: müşteriler ve siparişler](sample-xml-file-customers-orders.md).</span><span class="sxs-lookup"><span data-stu-id="a793f-111">The example uses XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md).</span></span>

```csharp
public class Customer
{
    private string customerID;
    public string CustomerID{ get{return customerID;} set{customerID = value;}}

    private string companyName;
    public string CompanyName{ get{return companyName;} set{companyName = value;}}

    private string contactName;
    public string ContactName { get{return contactName;} set{contactName = value;}}

    public Customer(string customerID, string companyName, string contactName)
    {
        CustomerID = customerID;
        CompanyName = companyName;
        ContactName = contactName;
    }

    public override string ToString()
    {
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement custOrd = XElement.Load("CustomersOrders.xml");
        IEnumerable<Customer> custList =
            from el in custOrd.Element("Customers").Elements("Customer")
            select new Customer(
                (string)el.Attribute("CustomerID"),
                (string)el.Element("CompanyName"),
                (string)el.Element("ContactName")
            );
        foreach (Customer cust in custList)
            Console.WriteLine(cust);
    }


}
```

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

<span data-ttu-id="a793f-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a793f-112">This example produces the following output:</span></span>

```output
GREAL:Great Lakes Food Market:Howard Snyder
HUNGC:Hungry Coyote Import Store:Yoshi Latimer
LAZYK:Lazy K Kountry Store:John Steel
LETSS:Let's Stop N Shop:Jaime Yorres
```

## <a name="see-also"></a><span data-ttu-id="a793f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a793f-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="a793f-114">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a793f-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
