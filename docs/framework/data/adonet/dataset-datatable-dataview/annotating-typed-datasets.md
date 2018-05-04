---
title: Yazılan veri kümeleri yorumlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 1974ac71e367203b8b94375e43d4fde13f2df51f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="annotating-typed-datasets"></a>Yazılan veri kümeleri yorumlama
Ek açıklamalar, yazılı öğeleri adlarını değiştirmek etkinleştirme <xref:System.Data.DataSet> temel şeması değiştirmeden. Temel alınan şemanızı öğeleri adları değiştirilmesi neden yazılı **DataSet** değil veri kaynağında mevcut yanı sıra veri kaynağında mevcut nesneleri başvuru kaybetmek nesneleri başvurmak için.  
  
 Ek açıklamalarını kullanma, nesnelerin adlarını, yazılı özelleştirebileceğiniz **DataSet** daha anlamlı adlarıyla kodunu daha okunabilir ve, yazılan hale **DataSet** bırakarak kullanmak istemcileri için daha kolay temel alınan şema kalır. Örneğin, aşağıdaki schema öğesi için **müşteriler** tablosu **Northwind** veritabanı sonuçlanacak bir **DataRow** nesne adını  **CustomersRow** ve <xref:System.Data.DataRowCollection> adlı **müşteriler**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **DataRowCollection** adını **müşteriler** istemci kodda anlamlı ancak **DataRow** adını **CustomersRow** yanıltıcıdır tek bir nesne olduğundan. Ayrıca, ortak senaryolar, nesne için olmadan başvurulabilir **satır** tanımlayıcısı ve bunun yerine yalnızca olarak adlandırılan bir **müşteri** nesnesi. Şema açıklama eklemek ve yeni adlarını tanımlamak için çözümdür **DataRow** ve **DataRowCollection** nesneleri. Aşağıdaki önceki şema açıklamalı sürümüdür.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Belirten bir **typedName** değerini **müşteri** sonuçlanır bir **DataRow** nesne adını **müşteri**. Belirten bir **typedPlural** değerini **müşteriler** korur **DataRowCollection** adını **müşteriler**.  
  
 Aşağıdaki tabloda kullanılabilir ek açıklamaları gösterilmektedir.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**typedName**|Nesnenin adı.|  
|**typedPlural**|Nesne koleksiyonu adı.|  
|**typedParent**|Bir üst ilişkisinde başvurulan zaman nesnesinin adı.|  
|**typedChildren**|Alt ilişkisi nesneleri döndürmek için yöntemin adı.|  
|**nullValue**|Temel alınan değer ise değer **DBNull**. İçin aşağıdaki tabloya bakın **nullValue** ek açıklamaları. Varsayılan değer **_throw**.|  
  
 İçin belirtilen değerler aşağıdaki tabloda gösterilmektedir **nullValue** ek açıklama.  
  
|nullValue değeri|Açıklama|  
|---------------------|-----------------|  
|*Değiştirme değeri*|Döndürülecek bir değer belirtin. Döndürülen değerin öğe türü eşleşmesi gerekir. Örneğin, `nullValue="0"` null tamsayı alanlar için 0 dönün.|  
|**_throw**|Bir özel durum. Bu varsayılandır.|  
|**_null**|Bir null başvuru dönün veya basit tür karşılaşılırsa, bir özel durum.|  
|**_empty**|Dizeler için iade **String.Empty**, aksi takdirde boş oluşturucudan oluşturulan bir nesne döndürür. Basit tür karşılaşılırsa, bir özel durum.|  
  
 Aşağıdaki tabloda nesneler için varsayılan değerleri yazılmış bir gösterilmektedir **DataSet** ve kullanılabilir ek açıklamaları.  
  
|Yöntem/nesnesi/olayı|Varsayılan|Ek Açıklama|  
|---------------------------|-------------|----------------|  
|**DataTable**|TableNameDataTable|typedPlural|  
|**DataTable** yöntemleri|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**DataRow**|TableNameRow|typedName|  
|**DataColumn**|DataTable.ColumnNameColumn<br /><br /> DataRow.ColumnName|typedName|  
|**Özelliği**|ÖzellikAdı|typedName|  
|**Alt** erişimcisi|GetChildTableNameRows|typedChildren|  
|**Üst** erişimcisi|TableNameRow|typedParent|  
|**Veri kümesi** olayları|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Kullanmak için yazılan **DataSet** ek açıklamalar, aşağıdaki içermelidir **xmlns** XML Şeması Tanım Dili (XSD) şeması başvurusu. (Bir xsd veritabanı tablolarından oluşturmak için bkz: <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](http://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Gösteren bir örnek açıklamalı şeması aşağıdadır **müşteriler** tablosu **Northwind** bir ilişkisine sahip veritabanı **siparişleri** dahil tablo.  
  
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
  
 Aşağıdaki kod örneğinde kesin türü belirtilmiş kullanan **DataSet** örnek şemadan oluşturuldu. Bir kullanan <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için **müşteriler** tablo ve başka <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için **siparişleri** tablo. Kesin türü belirtilmiş **DataSet** tanımlar **DataRelations**.  
  
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
    customers.Customers.NewCustomeromer()  
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
    customers.Customers.NewCustomeromer();  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [Türü Belirtilmiş DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
