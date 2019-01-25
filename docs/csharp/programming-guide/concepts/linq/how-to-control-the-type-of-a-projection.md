---
title: 'Nasıl yapılır: Bir projeksiyon türünü denetleme (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 020e847545d62709da091a9645d39f8fd0a5ce25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561029"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="290ae-102">Nasıl yapılır: Bir projeksiyon türünü denetleme (C#)</span><span class="sxs-lookup"><span data-stu-id="290ae-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="290ae-103">Yansıtma, bir veri kümesi alma, filtrelemesini, şeklini değiştirmek ve hatta da türünü değiştirmeyi işlemidir.</span><span class="sxs-lookup"><span data-stu-id="290ae-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="290ae-104">Çoğu sorgu ifadeleri tahminler gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="290ae-104">Most query expressions perform projections.</span></span> <span data-ttu-id="290ae-105">Bu bölümde gösterilen sorgu ifadeleri çoğunu değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, ancak diğer türler oluşturmak için projeksiyon türü denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="290ae-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="290ae-106">Bu konuda, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="290ae-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="290ae-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="290ae-107">Example</span></span>  
 <span data-ttu-id="290ae-108">Aşağıdaki örnek yeni bir tür tanımlar `Customer`.</span><span class="sxs-lookup"><span data-stu-id="290ae-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="290ae-109">Sorgu ifadesi sonra yeni başlatır `Customer` nesneler `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="290ae-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="290ae-110">Bu sorgu ifade türünü neden <xref:System.Collections.Generic.IEnumerable%601> , `Customer`.</span><span class="sxs-lookup"><span data-stu-id="290ae-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="290ae-111">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="290ae-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="290ae-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="290ae-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="290ae-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="290ae-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
- [<span data-ttu-id="290ae-114">Projeksiyonlar ve Dönüşümler (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="290ae-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
