---
title: 'Nasıl yapılır: Bir projeksiyon türünü denetleme (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 45f60934d6dcac5d2c0fa46409a773d8cdc8b6a2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487445"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Nasıl yapılır: Bir projeksiyon türünü denetleme (C#)
Yansıtma, bir veri kümesi alma, filtrelemesini, şeklini değiştirmek ve hatta da türünü değiştirmeyi işlemidir. Çoğu sorgu ifadeleri tahminler gerçekleştirin. Bu bölümde gösterilen sorgu ifadeleri çoğunu değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, ancak diğer türler oluşturmak için projeksiyon türü denetleyebilirsiniz. Bu konuda, bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir tür tanımlar `Customer`. Sorgu ifadesi sonra yeni başlatır `Customer` nesneler `Select` yan tümcesi. Bu sorgu ifade türünü neden <xref:System.Collections.Generic.IEnumerable%601> , `Customer`.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Müşteriler ve siparişler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
