---
description: 'Hakkında daha fazla bilgi edinin: bir veri kümesine mevcut kısıtlamalar ekleme'
title: DataSet’e Var Olan Kısıtlamaları Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: cad0dd1bd16747a5e76e10784d00c14cd9aa8c2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729579"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="73c33-103">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="73c33-103">Adding Existing Constraints to a DataSet</span></span>

<span data-ttu-id="73c33-104">**DataAdapter** 'ın **Fill** yöntemi bir <xref:System.Data.DataSet> veri kaynağından yalnızca tablo sütunları ve satırlar ile doldurulur; ancak kısıtlamalar veri kaynağı tarafından yaygın olarak ayarlanır, **Fill** yöntemi bu şema bilgilerini varsayılan olarak veri **kümesine** eklemez.</span><span class="sxs-lookup"><span data-stu-id="73c33-104">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="73c33-105">Bir veri **kümesini** bir veri kaynağından mevcut birincil anahtar kısıtlaması bilgileriyle doldurmak Için, **DataAdapter**'ın **FillSchema** metodunu çağırabilir ya da **Fill**' i çağırmadan önce **DataAdapter** 'ın **MissingSchemaAction** özelliğini **AddWithKey** olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73c33-105">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="73c33-106">Bu, veri **kümesindeki** birincil anahtar kısıtlamalarının veri kaynağında olanları yansıttığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="73c33-106">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="73c33-107">Yabancı anahtar kısıtlama bilgileri dahil değildir ve [DataTable kısıtlamalarında](./dataset-datatable-dataview/datatable-constraints.md)gösterildiği gibi açık bir şekilde oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73c33-107">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
<span data-ttu-id="73c33-108">Verilerle doldurulmadan önce şema bilgilerini bir veri **kümesine** eklemek, birincil anahtar kısıtlamalarının veri <xref:System.Data.DataTable> **kümesindeki** nesnelere dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="73c33-108">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="73c33-109">Sonuç olarak, veri **kümesini** dolduracak ek çağrılar yapıldığında, birincil anahtar sütun bilgileri her **DataTable**'daki geçerli satırlarla veri kaynağındaki yeni satırları eşleştirmek için kullanılır ve tablolardaki geçerli verilerin veri kaynağındaki verilerle üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="73c33-109">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="73c33-110">Şema bilgileri olmadan veri kaynağındaki yeni satırlar veri **kümesine** eklenir ve yinelenen satırlara yol açar.</span><span class="sxs-lookup"><span data-stu-id="73c33-110">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73c33-111">Bir veri kaynağındaki sütun otomatik artırma, **FillSchema** yöntemi veya WITH **AddWithKey** Için bir **MissingSchemaAction** ile **Fill** yöntemi olarak tanımlanırsa, bir **AutoIncrement** özelliği olarak ayarlanmış bir **DataColumn** oluşturur `true` .</span><span class="sxs-lookup"><span data-stu-id="73c33-111">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="73c33-112">Ancak, **oto ıncrementstep** ve **oto ıncrementseed** değerlerini kendiniz ayarlamanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="73c33-112">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="73c33-113">Sütunları otomatik artırma hakkında daha fazla bilgi için bkz. [AutoIncrement sütunları oluşturma](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="73c33-113">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
<span data-ttu-id="73c33-114">**FillSchema** kullanmak veya **MissingSchemaAction** 'ı **AddWithKey** olarak ayarlamak, birincil anahtar sütun bilgilerini belirlemede veri kaynağında fazladan işlem yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="73c33-114">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="73c33-115">Bu ek işlem performansı azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="73c33-115">This additional processing can hinder performance.</span></span> <span data-ttu-id="73c33-116">Tasarım zamanında birincil anahtar bilgilerini biliyorsanız, en iyi performansı elde etmek için birincil anahtar sütununu veya sütunları açıkça belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="73c33-116">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="73c33-117">Bir tabloya yönelik birincil anahtar bilgilerini açıkça ayarlama hakkında daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="73c33-117">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>
  
<span data-ttu-id="73c33-118">Aşağıdaki kod örneği, **FillSchema** kullanarak bir **veri kümesine** şema bilgilerinin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="73c33-118">The following code example shows how to add schema information to a **DataSet** using **FillSchema**:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
<span data-ttu-id="73c33-119">Aşağıdaki kod örneği, **Fill** yönteminin **MissingSchemaAction. AddWithKey** özelliğini kullanarak bir **veri kümesine** şema bilgilerinin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="73c33-119">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="73c33-120">Birden çok sonuç kümesini işleme</span><span class="sxs-lookup"><span data-stu-id="73c33-120">Handling multiple result sets</span></span>  

<span data-ttu-id="73c33-121">**DataAdapter** , **SelectCommand**'ten döndürülen birden çok sonuç kümesiyle karşılaşırsa, **veri kümesinde** birden çok tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73c33-121">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="73c33-122">Tablolar, "Table0" yerine **tablo** ile **başlayarak tablo** *N*' nin sıfır tabanlı artımlı varsayılan adı olarak verilecek.</span><span class="sxs-lookup"><span data-stu-id="73c33-122">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="73c33-123">Bir tablo adı **FillSchema** yöntemine bir bağımsız değişken olarak geçirilirse, tablolara "TableName0" yerine **TableName** ile başlayarak **TableName** *N*'nin sıfır tabanlı artımlı adı verilir.</span><span class="sxs-lookup"><span data-stu-id="73c33-123">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73c33-124">Birden çok sonuç kümesi döndüren bir komut için **OleDbDataAdapter** nesnesinin **FillSchema** yöntemi çağrılırsa, yalnızca ilk sonuç kümesinden şema bilgisi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="73c33-124">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="73c33-125">**OleDbDataAdapter** kullanarak birden çok sonuç kümesi için şema bilgilerini döndürürken, **AddWithKey** Için bir **MissingSchemaAction** belirtmeniz ve **Fill** metodunu çağırırken şema bilgilerini edinmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="73c33-125">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c33-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73c33-126">See also</span></span>

- [<span data-ttu-id="73c33-127">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="73c33-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="73c33-128">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="73c33-128">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="73c33-129">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="73c33-129">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="73c33-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="73c33-130">ADO.NET Overview</span></span>](ado-net-overview.md)
