---
description: 'Daha fazla bilgi edinin: Datareımımlarını gezinme'
title: DataRelations İçinde Gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 72d5bbb282b3b43434e528390769e1203519e8e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651814"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="e8b68-103">DataRelations İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="e8b68-103">Navigating DataRelations</span></span>

<span data-ttu-id="e8b68-104">' A ait birincil işlevlerden biri <xref:System.Data.DataRelation> , bir ' ın içinde diğerine gezinmesine izin verdir <xref:System.Data.DataTable> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="e8b68-104">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e8b68-105">Bu, <xref:System.Data.DataRow> ilgili bir **DataTable** nesnesinden tek bir **DataRow** verildiğinde ilgili tüm nesneleri bir **DataTable** içinde almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8b68-105">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="e8b68-106">Örneğin, bir müşteri tablosu ve sipariş tablosu arasında bir **DataRelation** oluşturduktan sonra, **GetChildRows** kullanarak belirli bir müşteri satırı için tüm sipariş satırlarını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8b68-106">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="e8b68-107">Aşağıdaki kod örneği, bir **veri kümesinin** **Customers** tablosu ve **Orders** tablosu arasında bir **DataRelation** oluşturur ve her müşteri için tüm siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8b68-107">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="e8b68-108">Sonraki örnek, dört tablo ile ilişkili ve bu ilişkilerle birlikte gelen örnek üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e8b68-108">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="e8b68-109">Önceki örnekte olduğu gibi, **MüşteriNo** , **Customers** tablosunu **Orders** tablosuyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="e8b68-109">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="e8b68-110">**Müşteriler** tablosundaki her müşteri Için, **siparişler** tablosundaki tüm alt satırlar, belirli bir müşterinin sahip olduğu siparişlerin sayısını ve bunların **OrderID** değerlerini döndürmek için belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e8b68-110">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="e8b68-111">Genişletilmiş örnek, **OrderDetails** ve **Products** tablolarından değerleri de döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8b68-111">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="e8b68-112">**Siparişler** tablosu, her müşteri siparişi, hangi ürünlerin ve miktarların sıralandığı hakkında bilgi edinmek için **OrderDetails** **tablosu ile ilgilidir** .</span><span class="sxs-lookup"><span data-stu-id="e8b68-112">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="e8b68-113">**OrderDetails** tablosu yalnızca sıralı bir ürünün **ProductID** 'Sini içerdiğinden, **OrderDetails** , **ProductName**'i döndürmek için **ProductID** kullanan **ürünlerle** ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="e8b68-113">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="e8b68-114">Bu ilişkide, **Ürünler** tablosu üst ve **sipariş ayrıntıları** tablosu alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="e8b68-114">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="e8b68-115">Sonuç olarak, **OrderDetails** tablosu üzerinden yineleme yaparken, ilgili **ProductName** değerini almak için **GetParentRow** çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e8b68-115">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="e8b68-116">**Müşteriler** ve **siparişler** tabloları Için **DataRelation** oluşturulduğunda, **createkısıtlamalar** bayrağı için hiçbir değer belirtildiğine dikkat edin (varsayılan değer **true**'dur).</span><span class="sxs-lookup"><span data-stu-id="e8b68-116">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="e8b68-117">Bu, **Orders** tablosundaki tüm satırların, ana **müşteriler** tablosunda bulunan bir **CustomerID** değeri olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="e8b68-117">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="e8b68-118">**Siparişler** tablosunda **müşteriler** tablosunda bulunmayan bir **CustomerID** varsa, bir <xref:System.Data.ForeignKeyConstraint> özel durumun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e8b68-118">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="e8b68-119">Alt sütun üst sütunun içermediği değerleri içeriyorsa, **DataRelation**'ı eklerken **createkısıtlamalar** bayrağını **false** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e8b68-119">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="e8b68-120">Örnekte, **Orders** tablosu ve **OrderDetails** tablosu arasındaki **DataRelation** için **createkısıtlamalar** bayrağı **false** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e8b68-120">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="e8b68-121">Bu, uygulamanın **OrderDetails** tablosundan tüm kayıtları ve bir çalışma zamanı özel durumu oluşturmadan **siparişler** tablosundan yalnızca bir kayıt alt kümesini döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8b68-121">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="e8b68-122">Genişletilmiş örnek, çıktıyı aşağıdaki biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e8b68-122">The expanded sample generates output in the following format.</span></span>  
  
```output  
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
  
 <span data-ttu-id="e8b68-123">Aşağıdaki kod örneği, sipariş **ayrıntıları** ve **ürün** tablolarından alınan değerlerin, yalnızca döndürülmekte olan **siparişler** tablosundaki kayıtların bir alt kümesiyle döndürüldüğü genişletilmiş bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e8b68-123">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e8b68-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8b68-124">See also</span></span>

- [<span data-ttu-id="e8b68-125">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="e8b68-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="e8b68-126">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e8b68-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
