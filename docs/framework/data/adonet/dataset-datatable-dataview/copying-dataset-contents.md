---
title: DataSet içeriklerini kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: b85fb6ebf56b110330be121c87d2492b0cfac536
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401950"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="f5095-102">DataSet içeriklerini kopyalama</span><span class="sxs-lookup"><span data-stu-id="f5095-102">Copying DataSet Contents</span></span>
<span data-ttu-id="f5095-103">Bir kopyasını oluşturabilirsiniz bir <xref:System.Data.DataSet> böylece özgün veriler etkilenmeden verileri ile çalışma veya iş verilerin bir alt kümesi ile bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="f5095-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="f5095-104">Kopyalama işlemi sırasında bir **veri kümesi**, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f5095-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="f5095-105">Tam bir kopyasını oluşturma **veri kümesi**şema, veri, satır durum bilgilerini ve satır sürümleri dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="f5095-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="f5095-106">Oluşturma bir **veri kümesi** varolan şema içeren **veri kümesi**, ancak yalnızca değiştirilen satırları.</span><span class="sxs-lookup"><span data-stu-id="f5095-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="f5095-107">Değiştirilmiş tüm satırları döndürür veya belirli bir belirtin **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="f5095-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="f5095-108">Satır durumları hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="f5095-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="f5095-109">Şema veya ilişkisel yapısını kopyası **veri kümesi** yalnızca, tüm satırları kopyalama olmadan.</span><span class="sxs-lookup"><span data-stu-id="f5095-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="f5095-110">Satırları, varolan içine aktarılabilir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5095-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="f5095-111">Tam bir kopyasını oluşturmak için **veri kümesi** hem şema hem de veri içeren, kullanın <xref:System.Data.DataSet.Copy%2A> yöntemi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="f5095-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="f5095-112">Aşağıdaki kod örneği, tam bir kopyasını oluşturma işlemi gösterilmektedir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="f5095-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="f5095-113">Bir kopyasını oluşturmak için bir **veri kümesi** içeren şema ve yalnızca verileri temsil eden **eklenen**, **değiştirilen**, veya **silinmiş** satır kullanın <xref:System.Data.DataSet.GetChanges%2A> yöntemi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="f5095-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="f5095-114">Ayrıca **GetChanges** geçirerek yalnızca belirtilen satır durumuna sahip satır döndürülecek bir **DataRowState** değer çağrılırken **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="f5095-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="f5095-115">Aşağıdaki kod örneğinde nasıl geçirileceğini gösterir. bir **DataRowState** çağırırken **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="f5095-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="f5095-116">Bir kopyasını oluşturmak için bir **veri kümesi** kullanmak, yalnızca şema içeren <xref:System.Data.DataSet.Clone%2A> yöntemi **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="f5095-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="f5095-117">Ayrıca var olan satır kopyalanan ekleyebilirsiniz **veri kümesi** kullanarak **ImportRow** yöntemi **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="f5095-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="f5095-118">**ImportRow** veri satırı durumu ve satır sürüm bilgilerini belirtilen tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="f5095-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="f5095-119">Sütun değerleri eklenir yalnızca sütun adı eşleştiği ve veri türü uyumludur.</span><span class="sxs-lookup"><span data-stu-id="f5095-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="f5095-120">Aşağıdaki kod örneği bir kopyasını oluşturur. bir **veri kümesi** ve ardından özgün satırları ekler **veri kümesi** için **müşteriler** tablosundaki **veri kümesi**  kopya müşteriler için burada **CountryRegion alanı** sütununun değeri "Germany".</span><span class="sxs-lookup"><span data-stu-id="f5095-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5095-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5095-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="f5095-122">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="f5095-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f5095-123">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f5095-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
