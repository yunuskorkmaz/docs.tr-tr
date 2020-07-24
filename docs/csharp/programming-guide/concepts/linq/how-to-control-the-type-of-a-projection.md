---
title: Projeksiyon türünü denetleme (C#)
description: LINQ XElement 'ten farklı türde Koleksiyonlar oluşturmak Için C# ' deki bir projeksiyonun türünü denetleme hakkında bilgi edinin <T> .
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103339"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="18440-103">Projeksiyon türünü denetleme (C#)</span><span class="sxs-lookup"><span data-stu-id="18440-103">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="18440-104">Projeksiyon, tek bir veri kümesini alma, filtreleme, şeklini değiştirme ve hatta türünü değiştirme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="18440-104">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="18440-105">Çoğu sorgu ifadesi tahminleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="18440-105">Most query expressions perform projections.</span></span> <span data-ttu-id="18440-106">Bu bölümde gösterilen sorgu ifadelerinin çoğu, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ' ın ' i değerlendirin, ancak başka türden Koleksiyonlar oluşturmak için projeksiyonun türünü kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18440-106">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="18440-107">Bu konuda bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="18440-107">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18440-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="18440-108">Example</span></span>  
 <span data-ttu-id="18440-109">Aşağıdaki örnek yeni bir türü tanımlar `Customer` .</span><span class="sxs-lookup"><span data-stu-id="18440-109">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="18440-110">Sorgu ifadesi daha sonra `Customer` yan tümcesinde yeni nesneler oluşturur `Select` .</span><span class="sxs-lookup"><span data-stu-id="18440-110">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="18440-111">Bu, sorgu ifadesinin türünün olmasına neden olur <xref:System.Collections.Generic.IEnumerable%601> `Customer` .</span><span class="sxs-lookup"><span data-stu-id="18440-111">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="18440-112">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="18440-112">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="18440-113">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="18440-113">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="18440-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18440-114">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
