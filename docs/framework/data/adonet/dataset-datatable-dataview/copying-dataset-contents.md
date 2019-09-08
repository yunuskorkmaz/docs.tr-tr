---
title: DataSet İçeriklerini Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: d8a7762c4ec5d650295ca0626180285723549051
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786520"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="8df9c-102">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="8df9c-102">Copying DataSet Contents</span></span>
<span data-ttu-id="8df9c-103">Özgün verileri etkilemeden verilerle çalışabilmeniz veya bir <xref:System.Data.DataSet> veri **kümesindeki**verilerin bir alt kümesiyle çalışmanız için bir kopyasını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8df9c-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="8df9c-104">Bir **veri kümesini**kopyalarken şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8df9c-104">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="8df9c-105">Şema, veri, satır durum bilgileri ve satır sürümleri dahil olmak üzere **veri kümesinin**tam bir kopyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8df9c-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="8df9c-106">Mevcut bir **veri kümesinin**şemasını Içeren bir **veri kümesi** oluşturun, ancak yalnızca değiştirilmiş olan satırları.</span><span class="sxs-lookup"><span data-stu-id="8df9c-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="8df9c-107">Değiştirilen tüm satırları döndürebilir veya belirli bir **DataRowState**belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8df9c-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="8df9c-108">Satır durumları hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="8df9c-108">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="8df9c-109">Herhangi bir satırı kopyalamadan yalnızca **veri kümesinin** şemasını veya ilişkisel yapısını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="8df9c-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="8df9c-110">Satırlar var olan <xref:System.Data.DataTable> bir using <xref:System.Data.DataTable.ImportRow%2A>öğesine aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="8df9c-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="8df9c-111">Hem şema hem de verileri içeren **veri kümesinin** tam bir kopyasını oluşturmak için, <xref:System.Data.DataSet.Copy%2A> **veri kümesinin**yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8df9c-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="8df9c-112">Aşağıdaki kod örneği, **veri kümesinin**tam bir kopyasının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8df9c-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="8df9c-113">Şemayı ve yalnızca **eklenen**, **değiştirilen**veya **silinen** satırları temsil eden verileri içeren bir <xref:System.Data.DataSet.GetChanges%2A> **veri kümesinin** kopyasını oluşturmak için, **veri kümesinin**yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8df9c-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="8df9c-114">**GetChanges 'ı çağırırken yalnızca**belirtilen satır durumundaki satırları döndürmek için **GetChanges** 'ı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8df9c-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="8df9c-115">Aşağıdaki kod örneği, **GetChanges**çağrılırken **DataRowState** 'in nasıl geçirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8df9c-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
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
  
 <span data-ttu-id="8df9c-116">Yalnızca şemayı içeren bir **veri kümesinin** kopyasını oluşturmak için <xref:System.Data.DataSet.Clone%2A> **veri kümesinin**yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8df9c-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="8df9c-117">Ayrıca, **DataTable**'ın **ImportRow** yöntemini kullanarak kopyalanan **veri kümesine** mevcut satırları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8df9c-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="8df9c-118">**ImportRow** , belirtilen tabloya veri, satır durumu ve satır sürümü bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="8df9c-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="8df9c-119">Sütun değerleri yalnızca sütun adının eşleştiği ve veri türünün uyumlu olduğu yerlerde eklenir.</span><span class="sxs-lookup"><span data-stu-id="8df9c-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="8df9c-120">Aşağıdaki kod örneği, bir **veri kümesinin** kopyasını oluşturur ve ardından orijinal **veri kümesindeki** satırları, **Ülke Bölgesi** sütununun "Almanya" değerine sahip olduğu müşteriler için **veri kümesi** kopyasının **müşteriler** tablosuna ekler. ".</span><span class="sxs-lookup"><span data-stu-id="8df9c-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8df9c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8df9c-121">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="8df9c-122">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8df9c-122">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8df9c-123">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8df9c-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
