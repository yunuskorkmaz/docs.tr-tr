---
title: DataTable'daki verileri görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: de745633060dd4f7b1610492d0ff57ec7a4f545b
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365393"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="446d7-102">DataTable'daki verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="446d7-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="446d7-103">İçeriğini erişebileceğiniz bir <xref:System.Data.DataTable> kullanarak **satırları** ve **sütunları** koleksiyonları **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="446d7-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="446d7-104">Ayrıca <xref:System.Data.DataTable.Select%2A> verilerin alt kümelerine döndürülecek yöntemi bir **DataTable** arama ölçütleri gibi ölçütlere göre sıralama düzeni ve satır durumu.</span><span class="sxs-lookup"><span data-stu-id="446d7-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="446d7-105">Ayrıca, kullanabileceğiniz <xref:System.Data.DataRowCollection.Find%2A> yöntemi **DataRowCollection** birincil bir anahtar değeri kullanarak belirli bir satır için arama yaparken.</span><span class="sxs-lookup"><span data-stu-id="446d7-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="446d7-106">**Seçin** yöntemi **DataTable** nesnesi döndüren bir dizi <xref:System.Data.DataRow> belirtilen ölçütlerle eşleşen nesneleri.</span><span class="sxs-lookup"><span data-stu-id="446d7-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="446d7-107">**Seçin** sıralama ifadesi bir filtre ifadesi, isteğe bağlı bağımsız değişkeni alır ve **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="446d7-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="446d7-108">Filtre ifadesi göre döndürülecek hangi satırların tanımlayan **DataColumn** gibi değerleri `LastName = 'Smith'`.</span><span class="sxs-lookup"><span data-stu-id="446d7-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="446d7-109">Sıralama ifadesi sütunları, örneğin sıralama için standart SQL kurallarına `LastName ASC, FirstName ASC`.</span><span class="sxs-lookup"><span data-stu-id="446d7-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="446d7-110">İfadeler yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="446d7-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="446d7-111">Çağrı sayısı gerçekleştiriyorsanız **seçin** yöntemi bir **DataTable**, ilk oluşturarak, performansı artırmak bir <xref:System.Data.DataView> için **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="446d7-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="446d7-112">Oluşturma **DataView** tablonun satırlarını dizinler.</span><span class="sxs-lookup"><span data-stu-id="446d7-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="446d7-113">**Seçin** yöntemi sonra dizin, usees sorgu sonucu üretmek için gereken süreyi önemli ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="446d7-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="446d7-114">Oluşturma hakkında daha fazla bilgi için bir **DataView** için bir **DataTable**, bkz: [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="446d7-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="446d7-115">**Seçin** yöntemi belirler satırları görüntülemek veya yönetmek için hangi sürümünün temel bir <xref:System.Data.DataViewRowState>.</span><span class="sxs-lookup"><span data-stu-id="446d7-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="446d7-116">Aşağıdaki tabloda olası açıklanmaktadır **DataViewRowState** sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="446d7-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="446d7-117">DataViewRowState değeri</span><span class="sxs-lookup"><span data-stu-id="446d7-117">DataViewRowState value</span></span>|<span data-ttu-id="446d7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="446d7-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="446d7-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="446d7-119">**CurrentRows**</span></span>|<span data-ttu-id="446d7-120">Geçerli satır değişmeden, eklenen ve değiştirilmiş satırları dahil etme.</span><span class="sxs-lookup"><span data-stu-id="446d7-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="446d7-121">**silindi**</span><span class="sxs-lookup"><span data-stu-id="446d7-121">**Deleted**</span></span>|<span data-ttu-id="446d7-122">Silinen bir satır.</span><span class="sxs-lookup"><span data-stu-id="446d7-122">A deleted row.</span></span>|  
|<span data-ttu-id="446d7-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="446d7-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="446d7-124">Özgün veri değiştirilmiş bir sürümü olan bir geçerli sürümü.</span><span class="sxs-lookup"><span data-stu-id="446d7-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="446d7-125">(Bkz **ModifiedOriginal**.)</span><span class="sxs-lookup"><span data-stu-id="446d7-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="446d7-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="446d7-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="446d7-127">Tüm değiştirilmiş satırları orijinal sürümü.</span><span class="sxs-lookup"><span data-stu-id="446d7-127">The original version of all modified rows.</span></span> <span data-ttu-id="446d7-128">Geçerli sürüm kullanılarak kullanılabilir **ModifiedCurrent**.</span><span class="sxs-lookup"><span data-stu-id="446d7-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="446d7-129">**Eklendi**</span><span class="sxs-lookup"><span data-stu-id="446d7-129">**Added**</span></span>|<span data-ttu-id="446d7-130">Yeni bir satır.</span><span class="sxs-lookup"><span data-stu-id="446d7-130">A new row.</span></span>|  
|<span data-ttu-id="446d7-131">**Yok**</span><span class="sxs-lookup"><span data-stu-id="446d7-131">**None**</span></span>|<span data-ttu-id="446d7-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="446d7-132">None.</span></span>|  
|<span data-ttu-id="446d7-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="446d7-133">**OriginalRows**</span></span>|<span data-ttu-id="446d7-134">Özgün satır, değişmez ve silinen satırları dahil etme.</span><span class="sxs-lookup"><span data-stu-id="446d7-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="446d7-135">**değişmedi**</span><span class="sxs-lookup"><span data-stu-id="446d7-135">**Unchanged**</span></span>|<span data-ttu-id="446d7-136">Değişmeyen bir satır.</span><span class="sxs-lookup"><span data-stu-id="446d7-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="446d7-137">Aşağıdaki örnekte, **veri kümesi** böylece yalnızca satır ile ayarlanmış çalıştığınız nesne filtrelenmiş **DataViewRowState** ayarlanır **CurrentRows**.</span><span class="sxs-lookup"><span data-stu-id="446d7-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 <span data-ttu-id="446d7-138">**Seçin** bakımından farklı olan satırlar döndürülecek yöntemi kullanılabilir **RowState** değerleri veya alan değerleri.</span><span class="sxs-lookup"><span data-stu-id="446d7-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="446d7-139">Aşağıdaki örnek döndüren bir **DataRow** silinmiş ve başka döndürür tüm satırları başvuran bir dizi **DataRow** sıralı başvuran tüm satırları, dizinin tarafından **CustLName**burada **CustId** sütun, 5'ten büyüktür.</span><span class="sxs-lookup"><span data-stu-id="446d7-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="446d7-140">Bilgileri görüntüleme hakkında bilgi için **silinmiş** satır bkz [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="446d7-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a><span data-ttu-id="446d7-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="446d7-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="446d7-142">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="446d7-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="446d7-143">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="446d7-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="446d7-144">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="446d7-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
