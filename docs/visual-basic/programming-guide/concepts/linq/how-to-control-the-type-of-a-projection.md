---
title: 'Nasıl yapılır: Projeksiyon Türünü Denetleme'
ms.date: 07/20/2015
ms.assetid: a0171276-0b46-4817-aee5-a8d5191b12fe
ms.openlocfilehash: 6b809188f68805afcca960bd809e079d997e79c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357263"
---
# <a name="how-to-control-the-type-of-a-projection-visual-basic"></a>Nasıl yapılır: projeksiyon türünü denetleme (Visual Basic)
Projeksiyon, tek bir veri kümesini alma, filtreleme, şeklini değiştirme ve hatta türünü değiştirme işlemidir. Çoğu sorgu ifadesi tahminleri gerçekleştirir. Bu bölümde gösterilen sorgu ifadelerinin çoğu, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> ' ın ' i değerlendirin, ancak başka türden Koleksiyonlar oluşturmak için projeksiyonun türünü kontrol edebilirsiniz. Bu konuda bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yeni bir türü tanımlar `Customer` . Sorgu ifadesi daha sonra `Customer` yan tümcesinde yeni nesneler oluşturur `Select` . Bu, sorgu ifadesinin türünün olmasına neden olur <xref:System.Collections.Generic.IEnumerable%601> `Customer` .  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: müşteriler ve siparişler (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).  
  
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
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Select%2A>
- [Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)](projections-and-transformations-linq-to-xml.md)
