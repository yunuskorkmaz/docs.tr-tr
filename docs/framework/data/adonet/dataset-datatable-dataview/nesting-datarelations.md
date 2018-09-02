---
title: İç içe geçme DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 9255615c7786773f1d4f453b910fdccdf191721f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420280"
---
# <a name="nesting-datarelations"></a>İç içe geçme DataRelations
Verilerin ilişkisel bir temsilini içinde tek tek tablolar, bir sütun veya sütun kümesini kullanarak birbirleriyle satırları içerir. ADO.NET'te <xref:System.Data.DataSet>, tablolar arasında ilişki kullanılarak uygulanan bir <xref:System.Data.DataRelation>. Oluştururken bir **DataRelation**, sütun üst-alt ilişkileri yalnızca ilişkisi yönetilir. Tabloları ve sütunları ayrı varlıklardır. XML sağlayan veri hiyerarşik temsili, iç içe geçmiş alt öğelerini içeren üst öğeler tarafından üst-alt ilişkilerini temsil edilir.  
  
 İç içe alt nesnelerin kolaylaştırmak için bir **veri kümesi** ile eşitlenen bir <xref:System.Xml.XmlDataDocument> veya XML verileri olarak kullanılarak yazılmış **WriteXml**, **DataRelation** kullanıma sunan bir **iç içe** özelliği. Ayarı **iç içe** özelliği bir **DataRelation** için **true** alt satırları XML verileri olarak yazılırken üst sütun içinde iç içe ilişkisinin neden olan veya eşitlenen bir **XmlDataDocument**. **İç içe** özelliği **DataRelation** olduğu **false**, varsayılan olarak.  
  
 Örneğin, aşağıdakileri dikkate alın **veri kümesi**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 Çünkü **iç içe** özelliği **DataRelation** nesnesi ayarlanmadı **true** bu **veri kümesi**, alt nesneler iç içe değil üst öğe içinde olduğunda bu **veri kümesi** XML verileri olarak temsil edilir. XML gösterimini dönüştürme bir **veri kümesi** içeren ilgili **veri kümesi**s ile iç içe veri ilişkileri performansın yavaşlamasına neden olabilir. Veri ilişkileri içe öneririz. Bunu yapmak için ayarlanmış **iç içe** özelliğini **true**. Ardından kod, yukarıdan aşağıya hiyerarşik XPath sorgu ifadeleri bulmak ve verileri dönüştürmek için kullandığı XSLT stil sayfası içinde yazın.  
  
 Aşağıdaki kod örneği, arama sonucu gösterir **WriteXml** üzerinde **veri kümesi**.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 Unutmayın **müşteriler** öğesi ve **siparişler** öğeleri Eşdüzey öğeleri olarak gösterilir. İsterseniz **siparişler** kendi ilgili üst öğelerinin alt öğe olarak gösterilecek öğeler **iç içe** özelliği **DataRelation** içinayarlanmışolmasıgerekir**true** ve aşağıdakileri ekleyin:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Aşağıdaki kod, ne elde edilen çıkış, şöyle görünmelidir gösterir ile **siparişler** öğeleri, ilgili üst öğeleri içinde iç içe geçmiş.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet içinde XML kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataRelations Ekleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
