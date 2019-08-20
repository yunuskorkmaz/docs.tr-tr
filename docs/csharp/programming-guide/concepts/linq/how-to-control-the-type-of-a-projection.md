---
title: 'Nasıl yapılır: Projeksiyon türünü denetleme (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 559cfb2a38ba76fb37a17100f0441498223852d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594028"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Nasıl yapılır: Projeksiyon türünü denetleme (C#)
Projeksiyon, tek bir veri kümesini alma, filtreleme, şeklini değiştirme ve hatta türünü değiştirme işlemidir. Çoğu sorgu ifadesi tahminleri gerçekleştirir. Bu bölümde gösterilen sorgu ifadelerinin çoğu, ' <xref:System.Collections.Generic.IEnumerable%601> ın <xref:System.Xml.Linq.XElement>' i değerlendirin, ancak başka türden Koleksiyonlar oluşturmak için projeksiyonun türünü kontrol edebilirsiniz. Bu konuda bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir türü `Customer`tanımlar. Sorgu ifadesi daha sonra `Customer` `Select` yan tümcesinde yeni nesneler oluşturur. Bu, sorgu ifadesinin <xref:System.Collections.Generic.IEnumerable%601> `Customer`türünün olmasına neden olur.  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Select%2A>
