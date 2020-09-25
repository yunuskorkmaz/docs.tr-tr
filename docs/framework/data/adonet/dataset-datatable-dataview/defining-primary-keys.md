---
title: Birincil Anahtarlar Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 94b033d58061e3d2e48a352d782eec7c4202fa43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166839"
---
# <a name="defining-primary-keys"></a>Birincil Anahtarlar Tanımlama

Veritabanı tablosu genellikle tablodaki her satırı benzersiz bir şekilde tanımlayan bir sütun veya sütun grubuna sahiptir. Bu tanımlayıcı sütun veya sütun grubuna birincil anahtar denir.  
  
 <xref:System.Data.DataColumn>Bir için tek bir olarak belirlediğinizde <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable> , tablo otomatik olarak <xref:System.Data.DataColumn.AllowDBNull%2A> sütunun özelliğini **yanlış** , <xref:System.Data.DataColumn.Unique%2A> özelliği de **true**olarak ayarlar. Birden çok sütunlu birincil anahtarlar için, yalnızca **AllowDBNull** özelliği otomatik olarak **false**olarak ayarlanır.  
  
 Bir öğesinin **PrimaryKey** özelliği, <xref:System.Data.DataTable> Aşağıdaki örneklerde gösterildiği gibi bir veya daha fazla **DataColumn** nesnesinin bir dizisi olarak alır. İlk örnek, birincil anahtar olarak tek bir sütunu tanımlar.  
  
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
  
 Aşağıdaki örnek, iki sütunu birincil anahtar olarak tanımlar.  
  
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
