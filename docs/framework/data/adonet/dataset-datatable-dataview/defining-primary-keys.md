---
title: Birincil Anahtarlar Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 84c84cb8fc0ee484b09c69c72571a19c335b58f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230635"
---
# <a name="defining-primary-keys"></a>Birincil Anahtarlar Tanımlama
Bir veritabanı tablosu, yaygın olarak bir sütun veya tablosundaki her satırda benzersiz olarak tanımlayan sütun grubunun sahiptir. Bu tanımlayıcı sütun veya sütun grubunun birincil anahtarı olarak adlandırılır.  
  
 Tanımlamak, tek bir <xref:System.Data.DataColumn> olarak <xref:System.Data.DataTable.PrimaryKey%2A> için bir <xref:System.Data.DataTable>, tablo otomatik olarak ayarlar <xref:System.Data.DataColumn.AllowDBNull%2A> sütununun özellik **false** ve <xref:System.Data.DataColumn.Unique%2A> özelliğini  **true**. Birden çok sütun birincil anahtarlar için yalnızca **AllowDBNull** otomatik olarak ayarlanırsa **false**.  
  
 **PrimaryKey** özelliği bir <xref:System.Data.DataTable> değeri olarak bir dizi bir veya daha fazla alan **DataColumn** , aşağıdaki örneklerde gösterildiği gibi nesneleri. İlk örnek, tek bir sütun birincil anahtar olarak tanımlar.  
  
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
  
 Aşağıdaki örnek, iki sütun birincil anahtar olarak tanımlar.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
