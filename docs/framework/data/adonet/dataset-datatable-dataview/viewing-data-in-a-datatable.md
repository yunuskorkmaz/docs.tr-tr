---
title: DataTable’daki Verileri Görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ea92b8a5e46bdaa8e94756cd28a3fbcb2789d7b3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204395"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="e408c-102">DataTable’daki Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e408c-102">Viewing Data in a DataTable</span></span>

<span data-ttu-id="e408c-103">**DataTable**'ın **Satırlar** ve **sütunlar** koleksiyonlarını kullanarak <xref:System.Data.DataTable> bir öğesinin içeriğine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e408c-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="e408c-104">Ayrıca, <xref:System.Data.DataTable.Select%2A> arama ölçütleri, sıralama düzeni ve satır durumu gibi ölçütlere göre **DataTable** içindeki verilerin alt kümelerini döndürmek için yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e408c-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="e408c-105">Ek olarak, bir birincil anahtar <xref:System.Data.DataRowCollection.Find%2A> değeri kullanarak belirli bir satırı ararken **DataRowCollection** yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e408c-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="e408c-106">**DataTable** nesnesinin <xref:System.Data.DataRow> **Select** yöntemi, belirtilen ölçütlerle eşleşen bir nesne kümesi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="e408c-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="e408c-107">Bir filtre ifadesinin, Sort ifadesinin ve **DataViewRowState**bağımsız değişkenlerini alır ' i **seçin** .</span><span class="sxs-lookup"><span data-stu-id="e408c-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="e408c-108">Filtre ifadesi,, `LastName = 'Smith'`gibi **DataColumn** değerlerine göre döndürülecek satırları belirler.</span><span class="sxs-lookup"><span data-stu-id="e408c-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="e408c-109">Sıralama ifadesi, örneğin `LastName ASC, FirstName ASC`sütunları SıRALAMAK için standart SQL kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="e408c-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="e408c-110">İfadeleri yazma hakkında kurallar için bkz <xref:System.Data.DataColumn.Expression%2A> . **DataColumn** sınıfının özelliği.</span><span class="sxs-lookup"><span data-stu-id="e408c-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="e408c-111">**DataTable**'ın <xref:System.Data.DataView> **Select** yöntemine bir dizi çağrı gerçekleştiriyorsanız, öncelikle **DataTable**için bir oluşturarak performansı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e408c-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="e408c-112">**DataView** oluşturmak tablo satırlarını dizine ekler.</span><span class="sxs-lookup"><span data-stu-id="e408c-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="e408c-113">**Select** yöntemi daha sonra bu dizini kullanır ve bu da sorgu sonucunu oluşturma süresini önemli ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="e408c-113">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="e408c-114">**DataTable**Için bir **DataView** oluşturma hakkında daha fazla bilgi için bkz. [DataView](dataviews.md).</span><span class="sxs-lookup"><span data-stu-id="e408c-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](dataviews.md).</span></span>

<span data-ttu-id="e408c-115">**Select** yöntemi, bir <xref:System.Data.DataViewRowState>öğesine göre hangi satır sürümünün görüntüleneceğini veya değiştirileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e408c-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="e408c-116">Aşağıdaki tabloda olası **DataViewRowState** numaralandırma değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e408c-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="e408c-117">DataViewRowState değeri</span><span class="sxs-lookup"><span data-stu-id="e408c-117">DataViewRowState value</span></span>|<span data-ttu-id="e408c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e408c-118">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="e408c-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="e408c-119">**CurrentRows**</span></span>|<span data-ttu-id="e408c-120">Değiştirilmemiş, eklenen ve değiştirilen satırları içeren geçerli satırlar.</span><span class="sxs-lookup"><span data-stu-id="e408c-120">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="e408c-121">**Miyor**</span><span class="sxs-lookup"><span data-stu-id="e408c-121">**Deleted**</span></span>|<span data-ttu-id="e408c-122">Silinen bir satır.</span><span class="sxs-lookup"><span data-stu-id="e408c-122">A deleted row.</span></span>|
|<span data-ttu-id="e408c-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="e408c-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="e408c-124">Özgün verilerin değiştirilmiş bir sürümü olan geçerli bir sürüm.</span><span class="sxs-lookup"><span data-stu-id="e408c-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="e408c-125">(Bkz. **Modifiedorijinal.** )</span><span class="sxs-lookup"><span data-stu-id="e408c-125">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="e408c-126">**Modifiedorijinal**</span><span class="sxs-lookup"><span data-stu-id="e408c-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="e408c-127">Değiştirilen tüm satırların orijinal sürümü.</span><span class="sxs-lookup"><span data-stu-id="e408c-127">The original version of all modified rows.</span></span> <span data-ttu-id="e408c-128">Geçerli sürüm, **ModifiedCurrent**kullanılarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e408c-128">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="e408c-129">**Eklenirse**</span><span class="sxs-lookup"><span data-stu-id="e408c-129">**Added**</span></span>|<span data-ttu-id="e408c-130">Yeni bir satır.</span><span class="sxs-lookup"><span data-stu-id="e408c-130">A new row.</span></span>|
|<span data-ttu-id="e408c-131">**Yok.**</span><span class="sxs-lookup"><span data-stu-id="e408c-131">**None**</span></span>|<span data-ttu-id="e408c-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="e408c-132">None.</span></span>|
|<span data-ttu-id="e408c-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="e408c-133">**OriginalRows**</span></span>|<span data-ttu-id="e408c-134">Değiştirilmemiş ve silinen satırlar dahil olmak üzere orijinal satırlar.</span><span class="sxs-lookup"><span data-stu-id="e408c-134">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="e408c-135">**Değiştirilmediği**</span><span class="sxs-lookup"><span data-stu-id="e408c-135">**Unchanged**</span></span>|<span data-ttu-id="e408c-136">Değiştirilmemiş bir satır.</span><span class="sxs-lookup"><span data-stu-id="e408c-136">An unchanged row.</span></span>|

<span data-ttu-id="e408c-137">Aşağıdaki örnekte, **veri kümesi** nesnesi filtrelenmiştir, böylece yalnızca **DataViewRowState** **CurrentRows**olarak ayarlanan satırlarla çalışmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e408c-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

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

<span data-ttu-id="e408c-138">**Select** yöntemi, farklı **RowState** değerlerini veya alan değerlerini içeren satırları döndürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e408c-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="e408c-139">Aşağıdaki örnek, silinmiş tüm satırlara başvuran bir **DataRow** dizisi döndürür ve CustId sütununun 5 ' ten büyük olduğu **CustLName**tarafından sıralanan tüm satırlara başvuran başka bir **DataRow** dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e408c-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="e408c-140">**Silinen** satırdaki bilgileri görüntüleme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="e408c-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e408c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e408c-141">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="e408c-142">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e408c-142">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="e408c-143">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="e408c-143">Row States and Row Versions</span></span>](row-states-and-row-versions.md)
- [<span data-ttu-id="e408c-144">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e408c-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
