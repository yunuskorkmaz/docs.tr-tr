---
title: "Satır durumları ve satır sürümleri"
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
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a56cae8b8e300b22a07184cdb69f2c876b101f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="row-states-and-row-versions"></a>Satır durumları ve satır sürümleri
ADO.NET satır durumları ve sürümleri kullanarak tablolardaki satırların yönetir. Bir satır durumu bir satır durumunu gösterir; Satır sürümleri, geçerli, özgün ve varsayılan değerler dahil olmak üzere değişiklik gibi bir satırda depolanan değerleri korur. Örneğin, bir satırda bir sütun yapılan bir değişikliği yaptıktan sonra satır satır durumunu olacaktır `Modified`, ve iki sürümleri satır: `Current`, geçerli satır değerleri içeren ve `Original`, sütun önce satır değerlerini içerir değiştirdi.  
  
 Her <xref:System.Data.DataRow> nesnesi bir <xref:System.Data.DataRow.RowState%2A> satır geçerli durumunu belirlemek için inceleyebilirsiniz özelliği. Aşağıdaki tabloda her kısa bir açıklamasını verir `RowState` numaralandırma değeri.  
  
|RowState değeri|Açıklama|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|Son çağrısından itibaren hiçbir değişiklik yapılmadı `AcceptChanges` veya satır tarafından oluşturulduktan sonra `DataAdapter.Fill`.|  
|<xref:System.Data.DataRowState.Added>|Tabloya satır eklendi ancak `AcceptChanges` çağrılmadıysa.|  
|<xref:System.Data.DataRowState.Modified>|Satırın bazı öğesi değiştirildi.|  
|<xref:System.Data.DataRowState.Deleted>|Bir tablodan satır silindi ve `AcceptChanges` çağrılmadıysa.|  
|<xref:System.Data.DataRowState.Detached>|Satırın herhangi bir parçası değil `DataRowCollection`. `RowState` Yeni oluşturulan bir satır kümesine `Detached`. Yeni sonra `DataRow` eklenen `DataRowCollection` çağırarak `Add` yöntemi, değeri `RowState` özelliği ayarlanmış `Added`.<br /><br /> `Detached`de kaldırıldığı bir satır için ayarlanmış bir `DataRowCollection` kullanarak `Remove` yöntemi, ya da `Delete` yöntemi arkasından `AcceptChanges` yöntemi.|  
  
 Zaman `AcceptChanges` üzerinde adlı bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , veya <xref:System.Data.DataRow>, satır durumuna sahip tüm satırları `Deleted` kaldırılır. Kalan satırlar satır durumunu verilen `Unchanged`ve değerler `Original` satır sürümü ile yazılır `Current` satır sürüm değerleri. Zaman `RejectChanges` çağrılır, satır durumuna sahip tüm satırları `Added` kaldırılır. Kalan satırlar satır durumunu verilen `Unchanged`ve değerler `Current` satır sürümü ile yazılır `Original` satır sürüm değerleri.  
  
 Bir satır farklı satır sürümlerini geçirerek görüntüleyebileceğiniz bir <xref:System.Data.DataRowVersion> aşağıdaki örnekte gösterildiği gibi sütun başvurusu parametresiyle.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 Aşağıdaki tabloda her kısa bir açıklamasını verir `DataRowVersion` numaralandırma değeri.  
  
|DataRowVersion değeri|Açıklama|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Satır için geçerli değerler. Bu satır sürümü satırlarla yok bir `RowState` , `Deleted`.|  
|<xref:System.Data.DataRowVersion.Default>|Belirli bir satır için varsayılan satır sürümü. Varsayılan satır sürümü için bir `Added`, `Modified`, veya `Unchanged` satır `Current`. Varsayılan satır sürümü için bir `Deleted` satır `Original`. Varsayılan satır sürümü için bir `Detached` satır `Proposed`.|  
|<xref:System.Data.DataRowVersion.Original>|Satırda özgün değerler. Bu satır sürümü satırlarla yok bir `RowState` , `Added`.|  
|<xref:System.Data.DataRowVersion.Proposed>|Satır için önerilen değerleri. Bir satırda ya da olmayan bir satır için bir düzenleme işlemi sırasında bu satır sürümü var. parçası bir `DataRowCollection`.|  
  
 Test edebilirsiniz olup bir `DataRow` çağırarak belirli bir satır sürümüne sahip <xref:System.Data.DataRow.HasVersion%2A> yöntemi ve geçirerek bir `DataRowVersion` bağımsız değişken olarak. Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` döndürülecek `false` önce yeni eklenen satırların `AcceptChanges` çağrıldı.  
  
 Aşağıdaki kod örneğinde, silinen içindeki tüm satırların bir tablonun değerlerini görüntüler. `Deleted`Satır sahip bir `Current` geçmesi gereken şekilde satır sürümü `DataRowVersion.Original` sütun değerlerini erişirken.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
