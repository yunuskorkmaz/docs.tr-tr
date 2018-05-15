---
title: Veri kümesi içeriği kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: bee91a6406fd48894580ce6223a5682dbadab380
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="87f3e-102">Veri kümesi içeriği kopyalama</span><span class="sxs-lookup"><span data-stu-id="87f3e-102">Copying DataSet Contents</span></span>
<span data-ttu-id="87f3e-103">Bir kopyasını oluşturabilirsiniz bir <xref:System.Data.DataSet> böylece iş verilerle özgün veriler etkilenmeden veya iş verilerini bir kümeyle bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="87f3e-104">Kopyalama işlemi sırasında bir **DataSet**, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87f3e-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="87f3e-105">Tam bir kopyasını oluşturmak **DataSet**şema, verileri, satır durumu bilgileri ve satır sürümleri dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="87f3e-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="87f3e-106">Oluşturma bir **DataSet** varolan şema içeren **DataSet**, ancak yalnızca değiştirilmiş satırları.</span><span class="sxs-lookup"><span data-stu-id="87f3e-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="87f3e-107">Değiştirilmiş tüm satırları döndürür veya belirli bir belirtin **DataRowState**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="87f3e-108">Satır durumları hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="87f3e-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="87f3e-109">Şema veya ilişkisel yapısı kopyası **DataSet** herhangi bir satır kopyalama olmadan yalnızca,.</span><span class="sxs-lookup"><span data-stu-id="87f3e-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="87f3e-110">Satırlar, var olan içine alınabilir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTable.ImportRow%2A>.</span><span class="sxs-lookup"><span data-stu-id="87f3e-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="87f3e-111">Tam bir kopyasını oluşturmak için **DataSet** hem şema hem de veri içeren, kullanın <xref:System.Data.DataSet.Copy%2A> yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="87f3e-112">Aşağıdaki kod örneğinde, tam bir kopyasını oluşturmak gösterilmiştir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="87f3e-113">Bir kopyasını oluşturmak için bir **DataSet** şema ve yalnızca verileri temsil eden içeren **eklenen**, **değiştirilen**, veya **silinmiş** satır kullanın <xref:System.Data.DataSet.GetChanges%2A> yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="87f3e-114">Aynı zamanda **GetChanges** geçirerek yalnızca satırları belirtilen satır durumuna döndürmek için bir **DataRowState** değer çağrılırken **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="87f3e-115">Aşağıdaki kod örneğinde nasıl iletileceğini gösterir bir **DataRowState** çağrılırken **GetChanges**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="87f3e-116">Bir kopyasını oluşturmak için bir **DataSet** yalnızca şema içeren, kullanın <xref:System.Data.DataSet.Clone%2A> yöntemi **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="87f3e-117">Ayrıca var olan satırları kopyalanan ekleyebilirsiniz **DataSet** kullanarak **ImportRow** yöntemi **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="87f3e-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="87f3e-118">**ImportRow** verileri, satır durumu ve satır sürüm bilgilerini belirtilen tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="87f3e-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="87f3e-119">Sütun değerleri eklenir yalnızca sütun adı eşleştiği ve veri türü uyumludur.</span><span class="sxs-lookup"><span data-stu-id="87f3e-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="87f3e-120">Aşağıdaki kod örneğinde bir kopyasını oluşturur bir **DataSet** ve sonra özgün satırları ekler **DataSet** için **müşteriler** tablosundaki **veri kümesi**  kopya müşteriler için burada **CountryRegion alanı** sütun "Almanya" değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="87f3e-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87f3e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87f3e-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="87f3e-122">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="87f3e-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="87f3e-123">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="87f3e-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
