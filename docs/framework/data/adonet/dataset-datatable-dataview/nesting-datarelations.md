---
title: "İç içe geçme DataRelations"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c057e836e8903fc2f5cb28f74858be97d2ffcc14
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-datarelations"></a>İç içe geçme DataRelations
İlişkisel bir veri içinde gösterimini tek tek tablolar birbirine bir sütun veya sütun kümesini kullanarak ilişkili satırları içerir. ADO.NET <xref:System.Data.DataSet>, tablolar arasında ilişki kullanılarak uygulanan bir <xref:System.Data.DataRelation>. Oluştururken bir **DataRelation**, sütun üst alt ilişkilerinde yalnızca ilişkisi yönetilir. Tablolar ve sütunlar ayrı varlıklardır. XML sağlayan veri hiyerarşik gösterimini üst alt ilişkilerinde iç içe geçmiş alt öğeleri içeren üst öğeler tarafından temsil edilir.  
  
 İç içe alt nesnelerin kolaylaştırmak için bir **DataSet** ile eşitlenen bir <xref:System.Xml.XmlDataDocument> veya XML verileri kullanarak olarak yazılmış **WriteXml**, **DataRelation** kullanıma sunan bir **iç içe** özelliği. Ayarı **iç içe** özelliği bir **DataRelation** için **true** alt satır XML verileri olarak yazılırken üst sütun içinde iç içe ilişkisinin neden olan veya eşitlenmiş bir **XmlDataDocument**. **İç içe** özelliği **DataRelation** olan **yanlış**, varsayılan olarak.  
  
 Örneğin, aşağıdakileri göz önünde bulundurun **DataSet**.  
  
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
  
 Çünkü **iç içe** özelliği **DataRelation** nesne ayarlı değil **true** bu **DataSet**, bağımlı nesneler iç içe değil üst öğeler içinde olduğunda bu **DataSet** XML verileri olarak temsil edilir. XML gösterimini dönüştürme bir **DataSet** içeren ilgili **DataSet**olmayan iç içe geçmiş veri ilişkileri s yavaş performans neden olabilir. Veri ilişkileri içe öneririz. Bunu yapmak için ayarlayın **iç içe** özelliğine **doğru**. Ardından kod bulun ve verileri dönüştürmek için yukarıdan aşağıya doğru hiyerarşik XPath sorgu ifadeleri kullanan XSLT stil sayfası yazın.  
  
 Aşağıdaki kod örneğinde arama sonuç gösterir **WriteXml** üzerinde **DataSet**.  
  
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
  
 Unutmayın **müşteriler** öğesi ve **siparişleri** öğeleri Eşdüzey öğeleri olarak gösterilir. İsterseniz **siparişleri** kendi ilgili üst öğeler alt öğesi olarak görüntülenmesini öğeleri **iç içe** özelliği **DataRelation** içinayarlanmışolmasıgerekir**doğru** ve aşağıdaki eklemeniz:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Aşağıdaki kod sonuçta çıktı gibi görünür gösterir ile **siparişleri** öğeleri, ilgili üst öğelerini içinde iç içe geçmiş.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
