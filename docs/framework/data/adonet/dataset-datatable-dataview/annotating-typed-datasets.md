---
title: Türü Belirtilmiş DataSets için Yorum Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 757a87f92d8dc6049de1844fed892d95dc57c990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151526"
---
# <a name="annotating-typed-datasets"></a>Türü Belirtilmiş DataSets için Yorum Ekleme
Ek açıklamalar, temel şemayı değiştirmeden yazdığınız <xref:System.Data.DataSet> öğelerin adlarını değiştirmenize olanak tanır. Temel şemanızdaki öğelerin adlarını değiştirmek, yazılan **DataSet'in** veri kaynağında bulunmayan nesnelere başvurmasının yanı sıra veri kaynağında bulunan nesnelere başvuruda bulunmasına neden olur.  
  
 Ek açıklamaları kullanarak, yazdığınız **DataSet'teki** nesnelerin adlarını daha anlamlı adlarla özelleştirerek kodu daha okunabilir hale getirebilir ve dakti-skar lı **DataSet'inizi** istemcilerin kullanmasını kolaylaştırırken, altta yatan şemayı bozulmadan bırakabilirsiniz. Örneğin, **Northwind** veritabanının **Müşteriler** tablosu için aşağıdaki şema **öğesi, CustomersRow'un** DataRow <xref:System.Data.DataRowCollection> nesne adı ve adlandırılmış **Müşteriler'in**bir **veritabanıyla** sonuçlanmasına neden olur.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **Müşterilerin** **DataRowCollection** adı istemci kodunda anlamlıdır, ancak Tek bir nesne olduğu için **CustomersRow'un** **DataRow** adı yanıltıcıdır. Ayrıca, yaygın senaryolarda, nesne **Satır** tanımlayıcısı olmadan başvurulur ve bunun yerine yalnızca **müşteri** nesnesi olarak adlandırılır. Çözüm şemayı açıklama yapmak ve DataRow ve **DataRowCollection** nesneleri **DataRowCollection** için yeni adlar tanımlamaktır. Aşağıda önceki şema açıklamalı sürümüdür.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **Müşterinin** **daktibName** değerinin belirtilmesi, **Müşterinin** **DataRow** nesne adı ile sonuçlanır. **Müşterilerin** **daktibÇoğul** değerini **belirtmek, Müşterilerin** **DataRowCollection** adını korur.  
  
 Aşağıdaki tabloda kullanılabilir ek açıklamalar gösterilmektedir.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**typedName**|Nesnenin adı.|  
|**typedPlural**|Nesneler koleksiyonunun adı.|  
|**typedParent**|Üst ilişkide atıfta bulunulduğunda nesnenin adı.|  
|**daktioÇocuklar**|Alt ilişkiden nesneleri döndürmek için yöntemin adı.|  
|**nullValue**|Temel değer **DBNull**ise değer. **NullValue** ek açıklamaları için aşağıdaki tabloya bakın. Varsayılan **_throw.**|  
  
 Aşağıdaki **tablo, nullValue** ek açıklama için belirtilen değerleri gösterir.  
  
|nullValue Değeri|Açıklama|  
|---------------------|-----------------|  
|*Değiştirme Değeri*|Döndürülecek bir değer belirtin. Döndürülen değer öğenin türüyle eşleşmelidir. Örneğin, null `nullValue="0"` integer alanları için 0 döndürmek için kullanın.|  
|**_throw**|Bir istisna at. Bu varsayılandır.|  
|**_null**|İlkel bir türle karşılaşılırsa, null başvurusu döndürün veya özel durum atın.|  
|**_empty**|Dizeleri için **String.Empty'ı**döndürün, aksi takdirde boş bir oluşturucudan oluşturulan bir nesneyi döndürün. İlkel bir türle karşılaşılırsa, bir özel durum atın.|  
  
 Aşağıdaki tablo, dakti-yazılı **DataSet'teki** nesneler ve kullanılabilir ek açıklamalar için varsayılan değerleri gösterir.  
  
|Nesne/Yöntem/Olay|Varsayılan|Ek Açıklama|  
|---------------------------|-------------|----------------|  
|**Datatable**|Tablo AdıDataTable|typedPlural|  
|**Veri Tablosu** Yöntemler|YeniTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**Datarowcollection**|TableName|typedPlural|  
|**Datarow**|TabloNameSatırı|typedName|  
|**Datacolumn**|DataTable.ColumnName<br /><br /> DataRow.ColumnName|typedName|  
|**Özellik**|ÖzellikAdı|typedName|  
|**Çocuk** Erişeni|GetChildTableNameRows|daktioÇocuklar|  
|**Ebeveyn** Erişeni|TabloNameSatırı|typedParent|  
|**Veri Seti** Olay|TabloNameSatır Değiştirme Etkinliği<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Yazılı **DataSet** ek açıklamalarını kullanmak için, XML Şema tanım dili (XSD) şemanıza aşağıdaki **xmlns** başvurularını eklemeniz gerekir. Veritabanı tablolarından bir xsd <xref:System.Data.DataSet.WriteXmlSchema%2A> oluşturmak için Visual Studio'da Datasets'e bakın veya [Veri Kümeleriyle Çalışma'ya bakın.](/visualstudio/data-tools/dataset-tools-in-visual-studio)  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Aşağıda, **Northwind** veritabanının **Müşteriler** tablosunu **Siparişler** tablosuyla ilgili olarak ortaya çıkaran örnek açıklamalı şema yer almaktadır.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 Aşağıdaki kod örneği, örnek şemadan oluşturulan güçlü bir şekilde yazılan bir **DataSet** kullanır. <xref:System.Data.SqlClient.SqlDataAdapter> Biri **Müşteriler** tablosunu doldurmak için, <xref:System.Data.SqlClient.SqlDataAdapter> diğeri de **Siparişler** tablosunu doldurmak için kullanır. Güçlü bir şekilde yazılan **DataSet,** **DataRelations'ı**tanımlar.  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [Türü Belirtilmiş DataSets](typed-datasets.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
