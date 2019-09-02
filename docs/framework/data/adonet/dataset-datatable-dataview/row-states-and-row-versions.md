---
title: Satır Durumları ve Satır Sürümleri
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 24d0d44f5964708164f89b0d9fa6c4c1aac7da0b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204510"
---
# <a name="row-states-and-row-versions"></a>Satır Durumları ve Satır Sürümleri
ADO.NET satır durumlarını ve sürümlerini kullanarak tablolardaki satırları yönetir. Satır durumu bir satırın durumunu belirtir; satır sürümleri, geçerli, orijinal ve varsayılan değerleri de dahil olmak üzere, değiştirildiğinde bir satırda depolanan değerleri korur. Örneğin, bir satırdaki bir sütunda değişiklik yaptıktan sonra, satırda satır durumu `Modified`ve iki satır sürümü vardır: `Current`, geçerli satır değerlerini içeren ve `Original`satır değerlerini içeren sütun değiştirilmelidir.  
  
 Her <xref:System.Data.DataRow> nesnenin, satırın <xref:System.Data.DataRow.RowState%2A> geçerli durumunu belirleyebilmek için incelemenize olanak tanıyan bir özelliği vardır. Aşağıdaki tabloda her `RowState` bir numaralandırma değerinin kısa bir açıklaması verilmiştir.  
  
|RowState değeri|Açıklama|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|`AcceptChanges` Satır`DataAdapter.Fill`oluşturulduğu veya bu yana yapılan son çağrıdan bu yana hiçbir değişiklik yapılmadı.|  
|<xref:System.Data.DataRowState.Added>|Satır tabloya eklenmiş, ancak `AcceptChanges` çağrılmadı.|  
|<xref:System.Data.DataRowState.Modified>|Satırın bazı öğeleri değiştirildi.|  
|<xref:System.Data.DataRowState.Deleted>|Satır bir tablodan silindi ve `AcceptChanges` çağrılmadı.|  
|<xref:System.Data.DataRowState.Detached>|Satır herhangi bir `DataRowCollection`parçası değil. Yeni oluşturulan satırın ' i olarak `Detached`ayarlanır. `RowState` `DataRow` `DataRowCollection` `RowState` Yöntemi çağırarak `Added`yeni öğesine eklendikten sonra özelliğin değeri olarak ayarlanır. `Add`<br /><br /> `Detached`, `DataRowCollection` yöntemi`Remove`kullanılarak `AcceptChanges` veya yöntemitarafındanizlenenbirsatıriçindeayarlanır.`Delete`|  
  
 `AcceptChanges` ,<xref:System.Data.DataTable> , Veya<xref:System.Data.DataRow>üzerinde çağrıldığında, satır durumu`Deleted` olan tüm satırlar kaldırılır. <xref:System.Data.DataSet> Kalan satırlara satır durumu `Unchanged`verilir ve satır `Current` sürümündeki değerlerin `Original` satır sürümü değerleriyle üzerine yazılır. Çağrıldığında, satır `Added` durumu olan tüm satırlar kaldırılır. `RejectChanges` Kalan satırlara satır durumu `Unchanged`verilir ve satır `Original` sürümündeki değerlerin `Current` satır sürümü değerleriyle üzerine yazılır.  
  
 Aşağıdaki örnekte gösterildiği gibi, sütun başvurusuyla bir <xref:System.Data.DataRowVersion> parametre geçirerek bir satırın farklı satır sürümlerini görüntüleyebilirsiniz.  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 Aşağıdaki tabloda her `DataRowVersion` bir numaralandırma değerinin kısa bir açıklaması verilmiştir.  
  
|DataRowVersion değeri|Açıklama|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|Satır için geçerli değerler. Bu satır sürümü `RowState` , `Deleted`içeren satırlar için mevcut değil.|  
|<xref:System.Data.DataRowVersion.Default>|Belirli bir satır için varsayılan satır sürümü. `Added`, ,Veya`Deleted` satırı`Current`için varsayılan satır sürümü. `Modified` `Detached` Bir`Proposed`satırın varsayılan satır sürümü.|  
|<xref:System.Data.DataRowVersion.Original>|Satır için özgün değerler. Bu satır sürümü `RowState` , `Added`içeren satırlar için mevcut değil.|  
|<xref:System.Data.DataRowVersion.Proposed>|Satır için önerilen değerler. Bu satır sürümü bir satırdaki düzenleme işlemi sırasında veya bir `DataRowCollection`parçası olmayan bir satır için mevcuttur.|  
  
 Yöntemini çağırarak ve `DataRow` bir`DataRowVersion` bağımsız değişken olarak geçirerek, bir 'nin belirli bir satır sürümüne sahip olup olmadığını test edebilirsiniz. <xref:System.Data.DataRow.HasVersion%2A> Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` çağrılmadan önce `AcceptChanges` yeni `false` eklenen satırlara dönecektir.  
  
 Aşağıdaki kod örneği, bir tablonun silinen tüm satırlarındaki değerleri görüntüler. `Deleted`satırların bir `Current` satır sürümü olmadığından, sütun değerlerine erişirken geçiş `DataRowVersion.Original` yapmanız gerekir.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
