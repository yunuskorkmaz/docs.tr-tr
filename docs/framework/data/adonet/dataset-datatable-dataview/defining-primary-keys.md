---
title: Birincil Anahtarlar Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151188"
---
# <a name="defining-primary-keys"></a>Birincil Anahtarlar Tanımlama
Veritabanı tablosunda genellikle tablodaki her satırı benzersiz olarak tanımlayan bir sütun veya sütun grubu bulunur. Bu tanımlayıcı sütun veya sütun grubu birincil anahtar olarak adlandırılır.  
  
 Bir tek <xref:System.Data.DataColumn> bir <xref:System.Data.DataTable.PrimaryKey%2A> için olarak <xref:System.Data.DataTable>tanımladığınızda , tablo <xref:System.Data.DataColumn.AllowDBNull%2A> otomatik olarak **yanlış** ve <xref:System.Data.DataColumn.Unique%2A> özelliği **doğru**sütunun özelliği ni ayarlar. Birden çok sütunlu birincil anahtarlar için yalnızca **AllowDBNull** özelliği otomatik olarak **false**olarak ayarlanır.  
  
 Bir a'nın <xref:System.Data.DataTable> **PrimaryKey** özelliği, aşağıdaki örneklerde gösterildiği gibi, bir veya daha fazla **DataColumn** nesnesi dizisini değeri olarak alır. İlk örnek, tek bir sütunu birincil anahtar olarak tanımlar.  
  
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
  
 Aşağıdaki örnekte, birincil anahtar olarak iki sütun tanımlanır.  
  
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
- [DataTable Şema Tanımı](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
