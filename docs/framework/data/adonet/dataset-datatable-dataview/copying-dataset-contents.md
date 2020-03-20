---
title: DataSet İçeriklerini Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151370"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="ca116-102">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="ca116-102">Copying DataSet Contents</span></span>
<span data-ttu-id="ca116-103">Özgün verileri etkilemeden <xref:System.Data.DataSet> verilerle çalışabilmeniz veya **bir DataSet'ten**gelen verilerin bir alt kümesiyle çalışabilmeniz için bir kopyasını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca116-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="ca116-104">**Bir DataSet'i**kopyalarken şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ca116-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="ca116-105">Şema, veri, satır durumu bilgileri ve satır sürümleri de dahil olmak üzere **DataSet'in**tam bir kopyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca116-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="ca116-106">Varolan bir **DataSet'in**şemasını içeren, ancak yalnızca değiştirilen satırları içeren bir **DataSet** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ca116-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="ca116-107">Değiştirilen tüm satırları döndürebilir veya belirli bir **DataRowState**belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca116-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="ca116-108">Satır durumları hakkında daha fazla bilgi için [Bkz. Satır Durumları ve Satır Sürümleri.](row-states-and-row-versions.md)</span><span class="sxs-lookup"><span data-stu-id="ca116-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="ca116-109">**Yalnızca DataSet'in** şemaveya ilişkisel yapısını, herhangi bir satır kopyalamadan kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ca116-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="ca116-110">Satırlar varolan <xref:System.Data.DataTable> bir kullanarak <xref:System.Data.DataTable.ImportRow%2A>içe aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca116-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="ca116-111">Hem şema hem de veri içeren **DataSet'in** tam <xref:System.Data.DataSet.Copy%2A> bir kopyasını oluşturmak için **DataSet'in**yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca116-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="ca116-112">Aşağıdaki kod **örneği, DataSet'in**tam bir kopyasının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca116-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="ca116-113">Şema ve yalnızca **Eklenen,** **Değiştirilen**veya **Silinmiş** satırları temsil eden verileri içeren bir <xref:System.Data.DataSet.GetChanges%2A> **DataSet** kopyasını oluşturmak için **DataSet**yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca116-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="ca116-114">GetChanges'ı ararken **DataRowState** değerini geçerek yalnızca belirli bir satır durumu olan satırları döndürmek için **GetChanges'ı** da kullanabilirsiniz. **GetChanges**</span><span class="sxs-lookup"><span data-stu-id="ca116-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="ca116-115">Aşağıdaki kod **örneği, GetChanges'ı**ararken **DataRowState'in** nasıl geçirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca116-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="ca116-116">Yalnızca şema içeren bir **DataSet** kopyasını oluşturmak için <xref:System.Data.DataSet.Clone%2A> **DataSet**yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca116-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="ca116-117">**DataTable'ın** **ImportRow** yöntemini kullanarak klonlanmış **DataSet'e** varolan satırları da ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca116-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="ca116-118">**ImportRow,** belirtilen tabloya veri, satır durumu ve satır sürüm bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="ca116-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="ca116-119">Sütun değerleri yalnızca sütun adının eşleştiği ve veri türünün uyumlu olduğu yerlerde eklenir.</span><span class="sxs-lookup"><span data-stu-id="ca116-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="ca116-120">Aşağıdaki kod örneği bir **DataSet** klonu oluşturur ve ardından **CountryRegion** sütununda "Almanya" değerine sahip müşteriler için **Veri Seti** klonunda orijinal **DataSet'ten** **müşteriler** tablosuna satırlar ekler.</span><span class="sxs-lookup"><span data-stu-id="ca116-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ca116-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca116-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="ca116-122">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="ca116-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ca116-123">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ca116-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
