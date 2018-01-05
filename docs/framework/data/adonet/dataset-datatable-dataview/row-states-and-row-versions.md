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
# <a name="row-states-and-row-versions"></a><span data-ttu-id="aa287-102">Satır durumları ve satır sürümleri</span><span class="sxs-lookup"><span data-stu-id="aa287-102">Row States and Row Versions</span></span>
<span data-ttu-id="aa287-103">ADO.NET satır durumları ve sürümleri kullanarak tablolardaki satırların yönetir.</span><span class="sxs-lookup"><span data-stu-id="aa287-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="aa287-104">Bir satır durumu bir satır durumunu gösterir; Satır sürümleri, geçerli, özgün ve varsayılan değerler dahil olmak üzere değişiklik gibi bir satırda depolanan değerleri korur.</span><span class="sxs-lookup"><span data-stu-id="aa287-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="aa287-105">Örneğin, bir satırda bir sütun yapılan bir değişikliği yaptıktan sonra satır satır durumunu olacaktır `Modified`, ve iki sürümleri satır: `Current`, geçerli satır değerleri içeren ve `Original`, sütun önce satır değerlerini içerir değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="aa287-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="aa287-106">Her <xref:System.Data.DataRow> nesnesi bir <xref:System.Data.DataRow.RowState%2A> satır geçerli durumunu belirlemek için inceleyebilirsiniz özelliği.</span><span class="sxs-lookup"><span data-stu-id="aa287-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="aa287-107">Aşağıdaki tabloda her kısa bir açıklamasını verir `RowState` numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="aa287-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="aa287-108">RowState değeri</span><span class="sxs-lookup"><span data-stu-id="aa287-108">RowState value</span></span>|<span data-ttu-id="aa287-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa287-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="aa287-110">Son çağrısından itibaren hiçbir değişiklik yapılmadı `AcceptChanges` veya satır tarafından oluşturulduktan sonra `DataAdapter.Fill`.</span><span class="sxs-lookup"><span data-stu-id="aa287-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="aa287-111">Tabloya satır eklendi ancak `AcceptChanges` çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="aa287-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="aa287-112">Satırın bazı öğesi değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="aa287-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="aa287-113">Bir tablodan satır silindi ve `AcceptChanges` çağrılmadıysa.</span><span class="sxs-lookup"><span data-stu-id="aa287-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="aa287-114">Satırın herhangi bir parçası değil `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="aa287-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="aa287-115">`RowState` Yeni oluşturulan bir satır kümesine `Detached`.</span><span class="sxs-lookup"><span data-stu-id="aa287-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="aa287-116">Yeni sonra `DataRow` eklenen `DataRowCollection` çağırarak `Add` yöntemi, değeri `RowState` özelliği ayarlanmış `Added`.</span><span class="sxs-lookup"><span data-stu-id="aa287-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="aa287-117">`Detached`de kaldırıldığı bir satır için ayarlanmış bir `DataRowCollection` kullanarak `Remove` yöntemi, ya da `Delete` yöntemi arkasından `AcceptChanges` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aa287-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="aa287-118">Zaman `AcceptChanges` üzerinde adlı bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , veya <xref:System.Data.DataRow>, satır durumuna sahip tüm satırları `Deleted` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="aa287-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="aa287-119">Kalan satırlar satır durumunu verilen `Unchanged`ve değerler `Original` satır sürümü ile yazılır `Current` satır sürüm değerleri.</span><span class="sxs-lookup"><span data-stu-id="aa287-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="aa287-120">Zaman `RejectChanges` çağrılır, satır durumuna sahip tüm satırları `Added` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="aa287-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="aa287-121">Kalan satırlar satır durumunu verilen `Unchanged`ve değerler `Current` satır sürümü ile yazılır `Original` satır sürüm değerleri.</span><span class="sxs-lookup"><span data-stu-id="aa287-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="aa287-122">Bir satır farklı satır sürümlerini geçirerek görüntüleyebileceğiniz bir <xref:System.Data.DataRowVersion> aşağıdaki örnekte gösterildiği gibi sütun başvurusu parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="aa287-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="aa287-123">Aşağıdaki tabloda her kısa bir açıklamasını verir `DataRowVersion` numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="aa287-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="aa287-124">DataRowVersion değeri</span><span class="sxs-lookup"><span data-stu-id="aa287-124">DataRowVersion value</span></span>|<span data-ttu-id="aa287-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa287-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="aa287-126">Satır için geçerli değerler.</span><span class="sxs-lookup"><span data-stu-id="aa287-126">The current values for the row.</span></span> <span data-ttu-id="aa287-127">Bu satır sürümü satırlarla yok bir `RowState` , `Deleted`.</span><span class="sxs-lookup"><span data-stu-id="aa287-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="aa287-128">Belirli bir satır için varsayılan satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="aa287-128">The default row version for a particular row.</span></span> <span data-ttu-id="aa287-129">Varsayılan satır sürümü için bir `Added`, `Modified`, veya `Unchanged` satır `Current`.</span><span class="sxs-lookup"><span data-stu-id="aa287-129">The default row version for an `Added`, `Modified`, or `Unchanged` row is `Current`.</span></span> <span data-ttu-id="aa287-130">Varsayılan satır sürümü için bir `Deleted` satır `Original`.</span><span class="sxs-lookup"><span data-stu-id="aa287-130">The default row version for a `Deleted` row is `Original`.</span></span> <span data-ttu-id="aa287-131">Varsayılan satır sürümü için bir `Detached` satır `Proposed`.</span><span class="sxs-lookup"><span data-stu-id="aa287-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="aa287-132">Satırda özgün değerler.</span><span class="sxs-lookup"><span data-stu-id="aa287-132">The original values for the row.</span></span> <span data-ttu-id="aa287-133">Bu satır sürümü satırlarla yok bir `RowState` , `Added`.</span><span class="sxs-lookup"><span data-stu-id="aa287-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="aa287-134">Satır için önerilen değerleri.</span><span class="sxs-lookup"><span data-stu-id="aa287-134">The proposed values for the row.</span></span> <span data-ttu-id="aa287-135">Bir satırda ya da olmayan bir satır için bir düzenleme işlemi sırasında bu satır sürümü var. parçası bir `DataRowCollection`.</span><span class="sxs-lookup"><span data-stu-id="aa287-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="aa287-136">Test edebilirsiniz olup bir `DataRow` çağırarak belirli bir satır sürümüne sahip <xref:System.Data.DataRow.HasVersion%2A> yöntemi ve geçirerek bir `DataRowVersion` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="aa287-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="aa287-137">Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` döndürülecek `false` önce yeni eklenen satırların `AcceptChanges` çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="aa287-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="aa287-138">Aşağıdaki kod örneğinde, silinen içindeki tüm satırların bir tablonun değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aa287-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="aa287-139">`Deleted`Satır sahip bir `Current` geçmesi gereken şekilde satır sürümü `DataRowVersion.Original` sütun değerlerini erişirken.</span><span class="sxs-lookup"><span data-stu-id="aa287-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa287-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa287-140">See Also</span></span>  
 [<span data-ttu-id="aa287-141">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="aa287-141">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="aa287-142">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="aa287-142">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="aa287-143">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="aa287-143">DataAdapters and DataReaders</span></span>](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="aa287-144">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="aa287-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
