---
title: Satır Durumları ve Satır Sürümleri
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 1b80ae78fad22989f99fb1e992d4978a192e0c66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204534"
---
# <a name="row-states-and-row-versions"></a>Satır Durumları ve Satır Sürümleri

ADO.NET satır durumlarını ve sürümlerini kullanarak tablolardaki satırları yönetir. Satır durumu bir satırın durumunu belirtir; satır sürümleri, geçerli, orijinal ve varsayılan değerleri de dahil olmak üzere, değiştirildiğinde bir satırda depolanan değerleri korur. Örneğin, bir satırdaki bir sütunda değişiklik yaptıktan sonra, satırda satır durumu `Modified` ve iki satır sürümü vardır: `Current` , geçerli satır değerlerini içeren ve `Original` sütun değiştirilmeden önce satır değerlerini içeren.  
  
 Her <xref:System.Data.DataRow> nesnenin, <xref:System.Data.DataRow.RowState%2A> satırın geçerli durumunu belirleyebilmek için incelemenize olanak tanıyan bir özelliği vardır. Aşağıdaki tabloda her bir numaralandırma değerinin kısa bir açıklaması verilmiştir `RowState` .  
  
|RowState değeri|Açıklama|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|`AcceptChanges`Satır oluşturulduğu veya bu yana yapılan son çağrıdan bu yana hiçbir değişiklik yapılmadı `DataAdapter.Fill` .|  
|<xref:System.Data.DataRowState.Added>|Satır tabloya eklenmiş, ancak `AcceptChanges` çağrılmadı.|  
|<xref:System.Data.DataRowState.Modified>|Satırın bazı öğeleri değiştirildi.|  
|<xref:System.Data.DataRowState.Deleted>|Satır bir tablodan silindi ve `AcceptChanges` çağrılmadı.|  
|<xref:System.Data.DataRowState.Detached>|Satır herhangi bir parçası değil `DataRowCollection` . `RowState`Yeni oluşturulan satırın ' i olarak ayarlanır `Detached` . `DataRow`Yöntemi çağırarak yeni öğesine eklendikten sonra `DataRowCollection` `Add` `RowState` özelliğin değeri olarak ayarlanır `Added` .<br /><br /> `Detached` , `DataRowCollection` yöntemi kullanılarak veya yöntemi tarafından izlenen bir satır için de ayarlanır `Remove` `Delete` `AcceptChanges` .|  
  
 `AcceptChanges`,, Veya üzerinde çağrıldığında <xref:System.Data.DataSet> , <xref:System.Data.DataTable> <xref:System.Data.DataRow> satır durumu olan tüm satırlar `Deleted` kaldırılır. Kalan satırlara satır durumu verilir `Unchanged` ve satır sürümündeki değerlerin satır `Original` `Current` sürümü değerleriyle üzerine yazılır. `RejectChanges`Çağrıldığında, satır durumu olan tüm satırlar `Added` kaldırılır. Kalan satırlara satır durumu verilir `Unchanged` ve satır sürümündeki değerlerin satır `Current` `Original` sürümü değerleriyle üzerine yazılır.  
  
 <xref:System.Data.DataRowVersion>Aşağıdaki örnekte gösterildiği gibi, sütun başvurusuyla bir parametre geçirerek bir satırın farklı satır sürümlerini görüntüleyebilirsiniz.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 Aşağıdaki tabloda her bir numaralandırma değerinin kısa bir açıklaması verilmiştir `DataRowVersion` .  
  
|DataRowVersion değeri|Açıklama|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Satır için geçerli değerler. Bu satır sürümü, içeren satırlar için mevcut değil `RowState` `Deleted` .|  
|<xref:System.Data.DataRowVersion.Default>|Belirli bir satır için varsayılan satır sürümü. `Added`, `Modified` , Veya satırı için varsayılan satır sürümü `Deleted` `Current` . Bir satırın varsayılan satır sürümü `Detached` `Proposed` .|  
|<xref:System.Data.DataRowVersion.Original>|Satır için özgün değerler. Bu satır sürümü, içeren satırlar için mevcut değil `RowState` `Added` .|  
|<xref:System.Data.DataRowVersion.Proposed>|Satır için önerilen değerler. Bu satır sürümü bir satırdaki düzenleme işlemi sırasında veya bir parçası olmayan bir satır için mevcuttur `DataRowCollection` .|  
  
 `DataRow` <xref:System.Data.DataRow.HasVersion%2A> Yöntemini çağırarak ve bir bağımsız değişken olarak geçirerek, bir 'nin belirli bir satır sürümüne sahip olup olmadığını test edebilirsiniz `DataRowVersion` . Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` `false` çağrılmadan önce yeni eklenen satırlara dönecektir `AcceptChanges` .  
  
 Aşağıdaki kod örneği, bir tablonun silinen tüm satırlarındaki değerleri görüntüler. `Deleted` satırların bir `Current` satır sürümü olmadığından, sütun değerlerine erişirken geçiş yapmanız gerekir `DataRowVersion.Original` .  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [DataSets, DataTables ve DataViews](index.md)
- [DataAdapters ve DataReaders](../dataadapters-and-datareaders.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
