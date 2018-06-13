---
title: DataRelation gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: c46007fb86a76405fd99d6e943779238d6885aa8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761434"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="47785-102">DataRelation gezinme</span><span class="sxs-lookup"><span data-stu-id="47785-102">Navigating DataRelations</span></span>
<span data-ttu-id="47785-103">Birincil işlevlerinden biri bir <xref:System.Data.DataRelation> Gezinti birinden izin <xref:System.Data.DataTable> içinde başka bir bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="47785-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="47785-104">Bu sayede tüm almak ilgili <xref:System.Data.DataRow> nesnelerini **DataTable** tek bir verildiğinde **DataRow** ilgili öğesinden **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="47785-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="47785-105">Örneğin, kurduktan sonra bir **DataRelation** Müşteriler tablosu ve Siparişler tablosu arasında kullanarak bir müşterinin satır için tüm sipariş satırları alabilirsiniz **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="47785-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="47785-106">Aşağıdaki kod örneği oluşturur bir **DataRelation** arasında **müşteriler** tablo ve **siparişleri** tablosunun bir **DataSet** ve döndürür Tüm siparişleri her müşteri için.</span><span class="sxs-lookup"><span data-stu-id="47785-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="47785-107">Sonraki örnek dört tablonun birlikte ilgili ve bu ilişkilerinde gezinme önceki örnekte üzerinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47785-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="47785-108">Önceki örnekte olduğu gibi **CustomerID** ilişkili **müşteriler** tablosu **siparişleri** tablo.</span><span class="sxs-lookup"><span data-stu-id="47785-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="47785-109">Her müşteri için **müşteriler** tablo, tüm alt satırları **siparişleri** tablo belirlenir, belirli bir müşterinin siparişleri sayısını döndürmek için ve bunların **OrderID** değerleri.</span><span class="sxs-lookup"><span data-stu-id="47785-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="47785-110">Genişletilmiş örnek değerleri de döndürür **sipariş ayrıntıları** ve **ürünleri** tabloları.</span><span class="sxs-lookup"><span data-stu-id="47785-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="47785-111">**Siparişleri** tablo ile ilgili **sipariş ayrıntıları** kullanarak tablo **OrderID** belirlemek için her biri için müşteri siparişi, hangi ürünler ve miktarları sipariş edilen.</span><span class="sxs-lookup"><span data-stu-id="47785-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="47785-112">Çünkü **sipariş ayrıntıları** tablosu yalnızca içerir **ProductID** sıralı, ürün **sipariş ayrıntıları** ilgili **ürünleri** kullanarak **ProductID** dönebilmek için **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="47785-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="47785-113">Bu ilişkiyi **ürünleri** üst bir tablodur ve **sipariş ayrıntılarını** tablodur alt.</span><span class="sxs-lookup"><span data-stu-id="47785-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="47785-114">Üzerinden yineleme olduğunda sonuç olarak, **sipariş ayrıntıları** tablo **GetParentRow** ilgili almak için çağrılır **ProductName** değeri.</span><span class="sxs-lookup"><span data-stu-id="47785-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="47785-115">Fark olduğunda **DataRelation** için oluşturulan **müşteriler** ve **siparişleri** tabloları, herhangi bir değer için belirtilmişse **createConstraints**bayrağını (varsayılan **true**).</span><span class="sxs-lookup"><span data-stu-id="47785-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="47785-116">Bu, tüm varsayar satırları **siparişleri** tablonuz bir **CustomerID** üst var. değer **müşteriler** tablo.</span><span class="sxs-lookup"><span data-stu-id="47785-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="47785-117">Varsa bir **CustomerID** bulunmaktadır **siparişleri** bulunmayan tablo **müşteriler** tablo, bir <xref:System.Data.ForeignKeyConstraint> bir özel durum oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="47785-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="47785-118">Alt sütun üst sütun içermiyor değerler içerebilecek ayarlanmadığında **createConstraints** bayrağını **false** eklerken **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="47785-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="47785-119">Örnekte, **createConstraints** bayrağı ayarlanmış **false** için **DataRelation** arasında **siparişleri** tablo ve  **Sipariş Ayrıntıları** tablo.</span><span class="sxs-lookup"><span data-stu-id="47785-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="47785-120">Bu uygulama tüm kayıtların dönüş sağlar **sipariş ayrıntıları** tablo ve yalnızca bir alt kümesini kayıtlarından **siparişleri** bir çalışma zamanı özel oluşturma olmadan tablo.</span><span class="sxs-lookup"><span data-stu-id="47785-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="47785-121">Genişletilmiş örnek aşağıdaki biçimde bir çıktı üretir.</span><span class="sxs-lookup"><span data-stu-id="47785-121">The expanded sample generates output in the following format.</span></span>  
  
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
  
 <span data-ttu-id="47785-122">Aşağıdaki kod örneğinde genişletilmiş bir örnektir burada değerleri **sipariş ayrıntıları** ve **ürünleri** tabloları döndürüldü, yalnızca bir alt kümesini kayıtları ile **siparişleri**döndürülen tablo.</span><span class="sxs-lookup"><span data-stu-id="47785-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="47785-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47785-123">See Also</span></span>  
 [<span data-ttu-id="47785-124">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="47785-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="47785-125">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="47785-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
