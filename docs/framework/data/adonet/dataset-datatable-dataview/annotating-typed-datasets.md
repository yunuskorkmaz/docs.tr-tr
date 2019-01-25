---
title: Türü belirtilmiş DataSets için yorum ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 737f98dd11d6172bb79aaa925ac153c64728e9ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629621"
---
# <a name="annotating-typed-datasets"></a>Türü belirtilmiş DataSets için yorum ekleme
Ek açıklamalar, belirlenmiş öğelerin adlarını değiştirmek etkinleştirme <xref:System.Data.DataSet> arka plandaki şema değiştirmeden. Temel alınan şemadaki öğelerin adlarını değiştirme neden belirlenmiş **veri kümesi** değil veri kaynağında mevcut yanı sıra veri kaynağında bulunan nesnelere başvuru kaybetmek nesneleri başvurmak için.  
  
 Ek açıklamalarını kullanma, nesnelerin adlarını, belirlenmiş özelleştirebileceğiniz **veri kümesi** daha anlamlı adlar ile kod daha okunabilir ve, belirlenmiş yapmadan **veri kümesi** bırakarak kullanmak istemcileri için daha kolay arka plandaki şema sağlam. Örneğin, aşağıdaki şema öğesi için **müşteriler** tablosu **Northwind** veritabanı sonuçlanır bir **DataRow** nesne adını  **CustomersRow** ve <xref:System.Data.DataRowCollection> adlı **müşteriler**.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 A **DataRowCollection** adını **müşteriler** istemci kodu, anlamlı ancak **DataRow** adını **CustomersRow** yanıltıcıdır tek bir nesne olduğu için. Ortak senaryolar nesnesi olmadan da **satır** tanımlayıcısı ve bunun yerine yalnızca olarak adlandırılan bir **müşteri** nesne. Şema Not ekleme ve yeni adlarını tanımlamak için çözümüdür **DataRow** ve **DataRowCollection** nesneleri. Ek açıklamalı önceki şema sürümü aşağıda verilmiştir.  
  
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
|**typedName**|Nesnesinin adı.|  
|**typedPlural**|Nesne koleksiyonu adı.|  
|**typedParent**|Üst ilişkisi içinde başvurulan nesne adı.|  
|**typedChildren**|Bir alt ilişkisi nesneleri döndürmek için yöntemin adı.|  
|**nullvalue &**|Temeldeki değeri ise değer **DBNull**. İçin aşağıdaki tabloya bakın **; nullvalue &** ek açıklamalar. Varsayılan değer **_throw**.|  
  
 Aşağıdaki tablo için belirtilen değerleri gösterir **; nullvalue &** ek açıklama.  
  
|nullvalue & değer|Açıklama|  
|---------------------|-----------------|  
|*Değiştirme değeri*|Döndürülecek bir değer belirtin. Döndürülen değer, öğe türü eşleşmesi gerekir. Örneğin, `nullValue="0"` 0 null tamsayı alanları için döndürülecek.|  
|**_throw**|Bir özel durum. Bu varsayılandır.|  
|**_null**|Null bir başvuru döndürmeyi veya ilkel tür mı yoksa bir özel durum.|  
|**_boş**|Dizeler için iade **String.Empty**, aksi takdirde boş bir oluşturucu oluşturulan bir nesne döndürür. Basit bir tür karşılaşılırsa, bir özel durum.|  
  
 Yazılmış bir nesneler için varsayılan değerleri aşağıdaki tabloda gösterilmektedir **veri kümesi** ve kullanılabilir ek açıklamalar.  
  
|Nesne/yöntemi/olay|Varsayılan|Ek Açıklama|  
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
  
 Kullanılacak yazılan **veri kümesi** ek açıklamaları, aşağıdakileri içermelidir **xmlns** , XML Şeması Tanım Dili (XSD) şemaya başvurusu. (Bir xsd veritabanı tabloları oluşturmak için bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> veya [Visual Studio'da veri kümeleriyle çalışma](https://msdn.microsoft.com/library/8bw9ksd6.aspx)).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Gösteren bir örnek açıklamalı Şeması aşağıdaki gibidir **müşteriler** tablosu **Northwind** bir ilişkisine veritabanıyla **siparişler** dahil tablo.  
  
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
  
 Aşağıdaki kod örneği, türü kesin belirlenmiş kullanan **veri kümesi** örnek şema oluşturuldu. Kullanan tek <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için **müşteriler** tablo ile diğeri <xref:System.Data.SqlClient.SqlDataAdapter> doldurmak için **siparişler** tablo. Kesin olarak belirlenmiş **veri kümesi** tanımlar **DataRelations**.  
  
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
- [Türü Belirtilmiş DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
