---
title: "Birincil anahtarlar tanımlama"
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2ba353353b52e5a866887e7f0dc4b743e336bd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-primary-keys"></a>Birincil anahtarlar tanımlama
Bir veritabanı tablosu genellikle bir sütun veya sütunlar tablodaki her satırda benzersiz olarak tanımlayan grubunun sahiptir. Bu tanımlayıcı sütun veya sütun grubunun birincil anahtar adı verilir.  
  
 Tanımlamak zaman tek bir <xref:System.Data.DataColumn> olarak <xref:System.Data.DataTable.PrimaryKey%2A> için bir <xref:System.Data.DataTable>, tablonun otomatik olarak ayarlar <xref:System.Data.DataColumn.AllowDBNull%2A> sütuna özelliğinin **false** ve <xref:System.Data.DataColumn.Unique%2A> özelliğine  **doğru**. Birden çok sütun birincil anahtarlar için yalnızca **AllowDBNull** özelliği ayarlanmış otomatik olarak **false**.  
  
 **PrimaryKey** özelliği bir <xref:System.Data.DataTable> değer olarak bir dizi bir veya daha fazla alan **DataColumn** , aşağıdaki örneklerde gösterildiği gibi nesneleri. İlk örnek tek bir sütun birincil anahtar olarak tanımlar.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 Aşağıdaki örnek, bir birincil anahtar olarak iki sütun tanımlar.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable>  
 [DataTable şema tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
