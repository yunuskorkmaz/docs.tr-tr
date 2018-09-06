---
title: DataRelations içinde gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 1819d468d12c03ce0c4faac11f4b20b8fe0f9c33
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43805695"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="535ee-102">DataRelations içinde gezinme</span><span class="sxs-lookup"><span data-stu-id="535ee-102">Navigating DataRelations</span></span>
<span data-ttu-id="535ee-103">Birincil işlevlerinden biri bir <xref:System.Data.DataRelation> bir gezinti izin vermesidir <xref:System.Data.DataTable> diğerine içinde bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="535ee-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="535ee-104">Bu sayede tüm almak ilgili <xref:System.Data.DataRow> birindeki nesnelerin **DataTable** tek bir verildiğinde **DataRow** ilgili gelen **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="535ee-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="535ee-105">Örneğin, kurduktan sonra bir **DataRelation** tablosu müşteriler ve Siparişler tablosunun arasında kullanarak bir müşterinin satır için tüm sipariş satırları alabilirsiniz **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="535ee-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="535ee-106">Aşağıdaki kod örneği oluşturur bir **DataRelation** arasında **müşteriler** tablo ve **siparişler** tablosunun bir **veri kümesi** ve döndürür Tüm siparişleri her müşteri için.</span><span class="sxs-lookup"><span data-stu-id="535ee-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="535ee-107">Sonraki örnekte, dört tablo birlikte ilgili ve bu ilişkilerinde gezinme önceki örnekte üzerinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="535ee-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="535ee-108">Önceki örnekte olduğu gibi **CustomerID** ilişkili **müşteriler** tablo **siparişler** tablo.</span><span class="sxs-lookup"><span data-stu-id="535ee-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="535ee-109">Her müşteri için **müşteriler** tablo, tüm alt satırları **siparişler** tablo belirlenir, belirli bir müşterinin siparişlerinin sayısını döndürmek için ve bunların **OrderID** değerleri.</span><span class="sxs-lookup"><span data-stu-id="535ee-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="535ee-110">Genişletilmiş örnek değerlerinin de döndürür **OrderDetails** ve **ürünleri** tablolar.</span><span class="sxs-lookup"><span data-stu-id="535ee-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="535ee-111">**Siparişler** tablo ilgili **OrderDetails** kullanarak tablo **OrderID** belirlemek için her biri için müşteri siparişi hangi ürün ve miktarların düzenlenebiliyordu.</span><span class="sxs-lookup"><span data-stu-id="535ee-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="535ee-112">Çünkü **OrderDetails** yalnızca tablo içeren **ProductID** sıralı bir ürünün **OrderDetails** ilgili **ürünleri** kullanarak **ProductID** döndürmek için **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="535ee-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="535ee-113">Bu ilişkiyi **ürünleri** üst tablodur ve **sipariş ayrıntıları** alt bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="535ee-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="535ee-114">Yineleme sırasında bir sonucu olarak **OrderDetails** tablo **GetParentRow** ilgili almak için çağırılır **ProductName** değeri.</span><span class="sxs-lookup"><span data-stu-id="535ee-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="535ee-115">Kullanırken dikkat edin **DataRelation** için oluşturulan **müşteriler** ve **siparişler** tablolar, herhangi bir değer için belirtilmişse **createConstraints**bayrağını (varsayılan değer **true**).</span><span class="sxs-lookup"><span data-stu-id="535ee-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="535ee-116">Bu, tüm varsayar satırlarda **siparişler** tablonuz bir **CustomerID** üst var. değer **müşteriler** tablo.</span><span class="sxs-lookup"><span data-stu-id="535ee-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="535ee-117">Varsa bir **CustomerID** var. **siparişler** yok tablo **müşteriler** tablo, bir <xref:System.Data.ForeignKeyConstraint> bir özel durum oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="535ee-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="535ee-118">Alt sütun üst sütun içermediğinden değerler içerdiğinde ayarlamak **createConstraints** bayrak **false** eklerken **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="535ee-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="535ee-119">Örnekte, **createConstraints** bayrağı ayarlandığında **false** için **DataRelation** arasında **siparişler** tablo ve  **OrderDetails** tablo.</span><span class="sxs-lookup"><span data-stu-id="535ee-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="535ee-120">Bu uygulamanın den tüm kayıtları döndüren sağlar **OrderDetails** tablo ve yalnızca bir alt kümesini kayıtlardan **siparişler** tablo olmadan bir çalışma zamanı özel durumu oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="535ee-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="535ee-121">Genişletilmiş örnek çıktısı aşağıdaki biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="535ee-121">The expanded sample generates output in the following format.</span></span>  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="535ee-122">Aşağıdaki kod örneği bir genişletilmiş bir örnektir burada değerlerinden **OrderDetails** ve **ürünleri** tablolar döndürülür, yalnızca bir alt kümesi ile kayıtlara **siparişler**döndürülen tablo.</span><span class="sxs-lookup"><span data-stu-id="535ee-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="535ee-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="535ee-123">See Also</span></span>  
 [<span data-ttu-id="535ee-124">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="535ee-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="535ee-125">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="535ee-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
