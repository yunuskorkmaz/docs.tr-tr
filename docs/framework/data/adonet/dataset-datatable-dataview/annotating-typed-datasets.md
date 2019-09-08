---
title: Türü Belirtilmiş DataSets için Yorum Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 351175b96d354a264a9280018ce21de8870beda2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784796"
---
# <a name="annotating-typed-datasets"></a>Türü Belirtilmiş DataSets için Yorum Ekleme
Ek açıklamalar, temeldeki şemayı değiştirmeden, yazdığınız <xref:System.Data.DataSet> öğelerin adlarını değiştirmenize olanak sağlar. Temel şemadaki öğelerin adlarını değiştirmek, yazılan veri **kümesinin** veri kaynağında mevcut olmayan nesnelere başvurmasına ve veri kaynağında var olan nesnelere yönelik bir başvuruyu kaybetmesine neden olur.  
  
 Ek açıklamaları kullanarak, yazılan **veri** kümenizdeki nesnelerin adlarını daha anlamlı adlarla özelleştirebilir, böylece kod daha okunabilir ve yazılan **Veri kümeniz** istemcilerin kullanması için daha kolay olur, temel şemayı bozulmadan bırakır. Örneğin, **Northwind** veritabanının **Customers** tablosu için aşağıdaki şema öğesi, **CustomersRow** ve <xref:System.Data.DataRowCollection> adlandırılmış **müşterilerin**bir **DataRow** nesne adı ile sonuçlanır.  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 Müşterilerin **DataRowCollection** adı istemci kodunda anlamlıdır, ancak tek bir nesne olduğundan **CustomersRow** **DataRow** adı yanıltıcı olur. Ayrıca, yaygın senaryolarda nesne, **satır** tanımlayıcı olmadan, bunun yerine yalnızca bir **Müşteri** nesnesi olarak adlandırılır. Çözüm, şemaya açıklama eklemek ve **DataRow** ve **DataRowCollection** nesnelerinin yeni adlarını belirlemektir. Önceki şemanın açıklamalı sürümü aşağıda verilmiştir.  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 **Müşterinin** **typedName** değerini belirtmek, bir **DataRow** nesnesinin **Müşteri**adına neden olur. **Müşteriler** Için **typedPlural** değeri belirtildiğinde **müşterilerin** **DataRowCollection** adı korunur.  
  
 Aşağıdaki tabloda kullanıma sunulan ek açıklamalar gösterilmektedir.  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**typedName**|Nesnenin adı.|  
|**typedPlural**|Bir nesne koleksiyonunun adı.|  
|**typedParent**|Üst ilişkide başvurulduğu sırada nesnenin adı.|  
|**typedChildren**|Bir alt ilişkiden nesneleri döndürmek için yöntemin adı.|  
|**nullValue**|Temel değer **DBNull**ise değeri. **NullValue** ek açıklamaları için aşağıdaki tabloya bakın. Varsayılan değer **_throw**' dir.|  
  
 Aşağıdaki tabloda, **NullValue** ek açıklaması için belirtime değerleri gösterilmektedir.  
  
|nullValue değeri|Açıklama|  
|---------------------|-----------------|  
|*Değiştirme değeri*|Döndürülecek bir değer belirtin. Döndürülen değerin öğe türüyle eşleşmesi gerekir. Örneğin, null tamsayı `nullValue="0"` alanları için 0 döndürmek üzere kullanın.|  
|**_throw**|Bir özel durum oluşturur. Bu varsayılandır.|  
|**_Null**|Bir temel tür ile karşılaşılırsa, null bir başvuru döndürün veya bir özel durum oluşturun.|  
|**_boş**|Dizeler için, **String. Empty**döndürün, aksi halde boş bir oluşturucudan oluşturulan nesneyi döndürün. İlkel bir tür ile karşılaşılırsa bir özel durum oluşturun.|  
  
 Aşağıdaki tabloda, türü belirtilmiş bir **veri kümesindeki** nesneler için varsayılan değerler ve kullanılabilir ek açıklamalar gösterilmektedir.  
  
|Nesne/yöntem/olay|Varsayılan|Ek Açıklama|  
|---------------------------|-------------|----------------|  
|**DataRow**|TableNameDataTable|typedPlural|  
|**DataTable** Yöntem|NewTableNameRow<br /><br /> AddTableNameRow<br /><br /> DeleteTableNameRow|typedName|  
|**DataRowCollection**|TableName|typedPlural|  
|**Nesnesinin**|TableNameRow|typedName|  
|**DataColumn**|DataTable. ColumnNameColumn<br /><br /> DataRow. ColumnName|typedName|  
|**Özelliði**|ÖzellikAdı|typedName|  
|**Alt öğe** Erişimci|GetChildTableNameRows|typedChildren|  
|**Üst öğe** Erişimci|TableNameRow|typedParent|  
|**Veri kümesi** Olayları|TableNameRowChangeEvent<br /><br /> TableNameRowChangeEventHandler|typedName|  
  
 Türü belirtilmiş **veri kümesi** ek açıklamalarını kullanmak Için XML şeması tanım DILI (xsd) şemanıza aşağıdaki **xmlns** başvurusunu eklemeniz gerekir. Veritabanı tablolarından bir xsd oluşturmak için bkz <xref:System.Data.DataSet.WriteXmlSchema%2A> . [Visual Studio 'da veri kümeleri ile çalışma](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 Aşağıda, **Northwind** veritabanının **Customers** tablosunu, dahil edilen **siparişler** tablosuyla bir ilişki ile kullanıma sunan örnek bir açıklamalı şema verilmiştir.  
  
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
  
 Aşağıdaki kod örneği, örnek şemadan oluşturulan kesin türü belirtilmiş bir **veri kümesini** kullanır. Bir tane, <xref:System.Data.SqlClient.SqlDataAdapter> **müşteriler** tablosunu doldurmak için bir tane kullanır <xref:System.Data.SqlClient.SqlDataAdapter> ve **Orders** tablosunu doldurmak için bir diğeri. Türü kesin belirlenmiş **veri kümesi** , **DataRelation**'ı tanımlar.  
  
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
