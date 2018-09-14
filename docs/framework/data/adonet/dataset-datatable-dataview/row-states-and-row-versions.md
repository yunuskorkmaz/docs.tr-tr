---
title: Satır durumları ve satır sürümleri
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 629e8b0bea1cd5c1dd80409acd7c03e0e033b5bc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560650"
---
# <a name="row-states-and-row-versions"></a>Satır durumları ve satır sürümleri
ADO.NET, tablolardaki satır durumları ve sürümlerini kullanarak satır yönetir. Bir satır durumu, bir satır durumunu gösterir; Satır sürümleri, geçerli ve özgün varsayılan değerleri dahil olmak üzere değişiklik gibi bir satır depolanan değerleri korur. Örneğin, bir satırda bir sütun için bir değişiklik yaptıktan sonra satır satır durumunu olur `Modified`, ve iki satır sürümleri: `Current`, geçerli satır değerleri içeren ve `Original`, sütun öncesinde satır değerleri içerir değiştirilmiş.  
  
 Her <xref:System.Data.DataRow> nesnesinin bir <xref:System.Data.DataRow.RowState%2A> satırın geçerli durumunu belirlemek için inceleyebilirsiniz özelliği. Aşağıdaki tabloda her kısa bir açıklaması verilmektedir `RowState` numaralandırma değeri.  
  
|RowState değeri|Açıklama|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Son çağrısından sonra herhangi bir değişiklik yapılmıştır `AcceptChanges` veya satır tarafından oluşturulduğundan beri `DataAdapter.Fill`.|  
|<xref:System.Data.DataRowState.Added>|Satır tabloya eklendi fakat `AcceptChanges` çağrılmadıysa.|  
|<xref:System.Data.DataRowState.Modified>|Satırın bazı öğesi değiştirildi.|  
|<xref:System.Data.DataRowState.Deleted>|Bir tablodan satır silindi ve `AcceptChanges` çağrılmadıysa.|  
|<xref:System.Data.DataRowState.Detached>|Satırın herhangi bir parçası değil `DataRowCollection`. `RowState` Yeni oluşturulan bir satır kümesine `Detached`. Sonra yeni `DataRow` eklenir `DataRowCollection` çağırarak `Add` yöntem, değeri `RowState` özelliği `Added`.<br /><br /> `Detached` kaldırılmış bir satır için de ayarlanmış bir `DataRowCollection` kullanarak `Remove` yöntemi veya `Delete` yöntemi arkasından `AcceptChanges` yöntemi.|  
  
 Zaman `AcceptChanges` üzerinde çağrılır bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , veya <xref:System.Data.DataRow>, satır durumuna sahip tüm satırları `Deleted` kaldırılır. Kalan satırlar satır durumunu verilen `Unchanged`ve değerleri `Original` satır sürümü ile yazılır `Current` satır sürümü değerleri. Zaman `RejectChanges` çağrılır, satır durumuna sahip tüm satırları `Added` kaldırılır. Kalan satırlar satır durumunu verilen `Unchanged`ve değerleri `Current` satır sürümü ile yazılır `Original` satır sürümü değerleri.  
  
 Bir satır farklı satır sürümlerini geçirerek görüntüleyebileceğiniz bir <xref:System.Data.DataRowVersion> parametresiyle aşağıdaki örnekte gösterildiği gibi sütun başvurusu.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 Aşağıdaki tabloda her kısa bir açıklaması verilmektedir `DataRowVersion` numaralandırma değeri.  
  
|DataRowVersion değeri|Açıklama|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Satır için geçerli değerleri. Bu satır sürümü ile satır için yok. bir `RowState` , `Deleted`.|  
|<xref:System.Data.DataRowVersion.Default>|Belirli bir satır için varsayılan satır sürümü. Varsayılan satır sürümü için bir `Added`, `Modified`, veya `Deleted` satır `Current`. Varsayılan satır sürümü için bir `Detached` satır `Proposed`.|  
|<xref:System.Data.DataRowVersion.Original>|Satır için özgün değer. Bu satır sürümü ile satır için yok. bir `RowState` , `Added`.|  
|<xref:System.Data.DataRowVersion.Proposed>|Satır için önerilen değerleri. Bir satırda veya olmayan bir satır için bir düzenleme işlemi sırasında bu satır sürümü var. parçası olan bir `DataRowCollection`.|  
  
 Test edebilirsiniz olup olmadığını bir `DataRow` çağırarak belirli bir satır sürümü olan <xref:System.Data.DataRow.HasVersion%2A> yöntemi ve geçirme bir `DataRowVersion` bağımsız değişken olarak. Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` döndüreceği `false` önce yeni eklenen satırlar için `AcceptChanges` çağrıldı.  
  
 Aşağıdaki kod örneği, tüm silinen satırları bir tablonun değerlerini görüntüler. `Deleted` satır yok bir `Current` geçmesi gerekir böylece satır sürümü `DataRowVersion.Original` sütun değerlerini erişirken.  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [DataAdapters ve DataReaders](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
