---
title: Projeksiyon türü nasıl kontrol edilebilen (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: cb7c272fbe67c0700b5740691befc483993f4e29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141357"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Projeksiyon türü nasıl kontrol edilebilen (C#)
Projeksiyon, bir veri kümesini alma, filtreleme, şeklini değiştirme ve hatta türünü değiştirme işlemidir. Sorgu ifadelerinin çoğu projeksiyonlar gerçekleştirir. Bu bölümde gösterilen sorgu ifadelerinin çoğu <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, ancak diğer tür koleksiyonları oluşturmak için projeksiyon türünü denetleyebilirsiniz. Bu konu, bunun nasıl yapılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte yeni bir `Customer`tür tanımlanır. Sorgu ifadesi daha sonra `Customer` `Select` yan tümcedeki yeni nesneleri anında inceler. Bu, sorgu ifadesinin türüne <xref:System.Collections.Generic.IEnumerable%601> `Customer`neden olur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Müşteriler ve Siparişler (LINQ-XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Select%2A>
