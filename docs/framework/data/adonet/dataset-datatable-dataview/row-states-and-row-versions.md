---
title: Satır durumları ve satır sürümleri
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 629e8b0bea1cd5c1dd80409acd7c03e0e033b5bc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880580"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="43917-102">Satır durumları ve satır sürümleri</span><span class="sxs-lookup"><span data-stu-id="43917-102">Row States and Row Versions</span></span>
<span data-ttu-id="43917-103">ADO.NET, tablolardaki satır durumları ve sürümlerini kullanarak satır yönetir.</span><span class="sxs-lookup"><span data-stu-id="43917-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="43917-104">Bir satır durumu, bir satır durumunu gösterir; Satır sürümleri, geçerli ve özgün varsayılan değerleri dahil olmak üzere değişiklik gibi bir satır depolanan değerleri korur.</span><span class="sxs-lookup"><span data-stu-id="43917-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="43917-105">Örneğin, bir satırda bir sütun için bir değişiklik yaptıktan sonra satır satır durumunu olur `Modified`, ve iki satır sürümleri: `Current`, geçerli satır değerleri içeren ve `Original`, sütun öncesinde satır değerleri içerir değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="43917-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="43917-106">Her <xref:System.Data.DataRow> nesnesinin bir <xref:System.Data.DataRow.RowState%2A> satırın geçerli durumunu belirlemek için inceleyebilirsiniz özelliği.</span><span class="sxs-lookup"><span data-stu-id="43917-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="43917-107">Aşağıdaki tabloda her kısa bir açıklaması verilmektedir `RowState` numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="43917-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="43917-108">RowState değeri</span><span class="sxs-lookup"><span data-stu-id="43917-108">RowState value</span></span>|<span data-ttu-id="43917-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43917-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="43917-110">Son çağrısından sonra herhangi bir değişiklik yapılmıştır `AcceptChanges` veya satır tarafından oluşturulduğundan beri `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="43917-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="43917-111">Satır tabloya eklendi fakat `AcceptChanges` çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="43917-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="43917-112">Satırın bazı öğesi değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="43917-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="43917-113">Bir tablodan satır silindi ve `AcceptChanges` çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="43917-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="43917-114">Satırın herhangi bir parçası değil `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="43917-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="43917-115">`RowState` Yeni oluşturulan bir satır kümesine `Detached`.</span><span class="sxs-lookup"><span data-stu-id="43917-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="43917-116">Sonra yeni `DataRow` eklenir `DataRowCollection` çağırarak `Add` yöntem, değeri `RowState` özelliği `Added`.</span><span class="sxs-lookup"><span data-stu-id="43917-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="43917-117">`Detached` kaldırılmış bir satır için de ayarlanmış bir `DataRowCollection` kullanarak `Remove` yöntemi veya `Delete` yöntemi arkasından `AcceptChanges` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="43917-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="43917-118">Zaman `AcceptChanges` üzerinde çağrılır bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , veya <xref:System.Data.DataRow>, satır durumuna sahip tüm satırları `Deleted` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="43917-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="43917-119">Kalan satırlar satır durumunu verilen `Unchanged`ve değerleri `Original` satır sürümü ile yazılır `Current` satır sürümü değerleri.</span><span class="sxs-lookup"><span data-stu-id="43917-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="43917-120">Zaman `RejectChanges` çağrılır, satır durumuna sahip tüm satırları `Added` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="43917-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="43917-121">Kalan satırlar satır durumunu verilen `Unchanged`ve değerleri `Current` satır sürümü ile yazılır `Original` satır sürümü değerleri.</span><span class="sxs-lookup"><span data-stu-id="43917-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="43917-122">Bir satır farklı satır sürümlerini geçirerek görüntüleyebileceğiniz bir <xref:System.Data.DataRowVersion> parametresiyle aşağıdaki örnekte gösterildiği gibi sütun başvurusu.</span><span class="sxs-lookup"><span data-stu-id="43917-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="43917-123">Aşağıdaki tabloda her kısa bir açıklaması verilmektedir `DataRowVersion` numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="43917-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="43917-124">DataRowVersion değeri</span><span class="sxs-lookup"><span data-stu-id="43917-124">DataRowVersion value</span></span>|<span data-ttu-id="43917-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43917-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="43917-126">Satır için geçerli değerleri.</span><span class="sxs-lookup"><span data-stu-id="43917-126">The current values for the row.</span></span> <span data-ttu-id="43917-127">Bu satır sürümü ile satır için yok. bir `RowState` , `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="43917-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="43917-128">Belirli bir satır için varsayılan satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="43917-128">The default row version for a particular row.</span></span> <span data-ttu-id="43917-129">Varsayılan satır sürümü için bir `Added`, `Modified`, veya `Deleted` satır `Current`.</span><span class="sxs-lookup"><span data-stu-id="43917-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="43917-130">Varsayılan satır sürümü için bir `Detached` satır `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="43917-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="43917-131">Satır için özgün değer.</span><span class="sxs-lookup"><span data-stu-id="43917-131">The original values for the row.</span></span> <span data-ttu-id="43917-132">Bu satır sürümü ile satır için yok. bir `RowState` , `Added`.</span><span class="sxs-lookup"><span data-stu-id="43917-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="43917-133">Satır için önerilen değerleri.</span><span class="sxs-lookup"><span data-stu-id="43917-133">The proposed values for the row.</span></span> <span data-ttu-id="43917-134">Bir satırda veya olmayan bir satır için bir düzenleme işlemi sırasında bu satır sürümü var. parçası olan bir `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="43917-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="43917-135">Test edebilirsiniz olup olmadığını bir `DataRow` çağırarak belirli bir satır sürümü olan <xref:System.Data.DataRow.HasVersion%2A> yöntemi ve geçirme bir `DataRowVersion` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="43917-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="43917-136">Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` döndüreceği `false` önce yeni eklenen satırlar için `AcceptChanges` çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="43917-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="43917-137">Aşağıdaki kod örneği, tüm silinen satırları bir tablonun değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43917-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="43917-138">`Deleted` satır yok bir `Current` geçmesi gerekir böylece satır sürümü `DataRowVersion.Original` sütun değerlerini erişirken.</span><span class="sxs-lookup"><span data-stu-id="43917-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43917-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43917-139">See Also</span></span>  
 [<span data-ttu-id="43917-140">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="43917-140">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="43917-141">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="43917-141">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="43917-142">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="43917-142">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="43917-143">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="43917-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
