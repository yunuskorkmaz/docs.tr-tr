---
title: DataTables
description: Bir ADO.NET DataTable hakkında bilgi edinin. Bu, bir bellek içi ilişkisel verilerin bir tablosunu ' de yerel olarak temsil eder. Bulunduğu yerde NET tabanlı uygulama.
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: d501096b4abe94653acdc5249c120abff94534d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202311"
---
# <a name="datatables"></a><span data-ttu-id="6f726-103">DataTables</span><span class="sxs-lookup"><span data-stu-id="6f726-103">DataTables</span></span>

<span data-ttu-id="6f726-104">Bir <xref:System.Data.DataSet> tablo, ilişki ve kısıtlama koleksiyonundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f726-104">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="6f726-105">ADO.NET ' de <xref:System.Data.DataTable> nesneler, bir **veri kümesindeki**tabloları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f726-105">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="6f726-106">**DataTable** , bellek içi ilişkisel verilerin bir tablosunu temsil eder; verileri yereldir. İçinde bulunduğu, ancak **DataAdapter** kullanarak Microsoft SQL Server bir veri kaynağından doldurulabilen, daha fazla bilgi için bkz. veri [kümesini DataAdapter 'tan doldurma](../populating-a-dataset-from-a-dataadapter.md).</span><span class="sxs-lookup"><span data-stu-id="6f726-106">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="6f726-107">**DataTable** sınıfı, .NET Framework sınıf kitaplığı içindeki **System. Data** ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="6f726-107">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="6f726-108">Bir **DataTable** 'ı bağımsız olarak veya bir **veri kümesinin**üyesi olarak oluşturabilir ve kullanabilirsiniz ve **datatable** nesneleri de dahil diğer .NET Framework nesneleriyle birlikte kullanılabilir <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="6f726-108">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="6f726-109">**DataSet nesnesinin** **Tables** özelliği aracılığıyla bir **veri kümesindeki** tablo koleksiyonuna erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f726-109">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="6f726-110">Bir tablonun şeması veya yapısı, sütunlar ve kısıtlamalar ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6f726-110">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="6f726-111">Nesneleri ve nesneleri kullanarak bir **DataTable** şemasını tanımlarsınız <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint> .</span><span class="sxs-lookup"><span data-stu-id="6f726-111">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="6f726-112">Bir tablodaki sütunlar bir veri kaynağındaki sütunlarla eşlenir, deyimlerden hesaplanan değerler içerebilir, değerlerini otomatik olarak artırır veya birincil anahtar değerleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6f726-112">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="6f726-113">Bir şemanın yanı sıra, bir **DataTable** 'ın de verileri içermesi ve sıralamak için satırları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f726-113">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="6f726-114"><xref:System.Data.DataRow>Sınıfı, bir tabloda bulunan gerçek verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f726-114">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="6f726-115">Bir tablodaki verileri almak, değerlendirmek ve işlemek için **DataRow** ve özelliklerini ve yöntemlerini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f726-115">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="6f726-116">Bir satır içindeki verileri erişirken ve değiştirirken, **DataRow** nesnesi hem geçerli hem de orijinal durumunu korur.</span><span class="sxs-lookup"><span data-stu-id="6f726-116">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="6f726-117">Tablolarda bir veya daha fazla ilişkili sütun kullanarak tablolar arasında üst-alt ilişkileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f726-117">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="6f726-118">Kullanarak **DataTable** nesneleri arasında bir ilişki oluşturursunuz <xref:System.Data.DataRelation> .</span><span class="sxs-lookup"><span data-stu-id="6f726-118">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="6f726-119">Daha sonra, belirli bir satırın ilişkili alt veya üst satırlarını döndürmek için **DataRelation** nesneleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f726-119">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="6f726-120">Daha fazla bilgi için bkz. [DataRelation 'ı ekleme](adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="6f726-120">For more information, see [Adding DataRelations](adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f726-121">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6f726-121">In This Section</span></span>  

 [<span data-ttu-id="6f726-122">DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f726-122">Creating a DataTable</span></span>](creating-a-datatable.md)  
 <span data-ttu-id="6f726-123">**DataTable** oluşturmayı ve bir **veri kümesine**eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f726-123">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="6f726-124">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="6f726-124">DataTable Schema Definition</span></span>](datatable-schema-definition.md)  
 <span data-ttu-id="6f726-125">**DataColumn** nesneleri ve kısıtlamalarını oluşturma ve kullanma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-125">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="6f726-126">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="6f726-126">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="6f726-127">Bir tablodaki verilerin nasıl ekleneceğini, değiştirileceğini ve silineceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f726-127">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="6f726-128">Tablodaki verilerde yapılan değişiklikleri incelemek için **DataTable** olaylarının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f726-128">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="6f726-129">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="6f726-129">Handling DataTable Events</span></span>](handling-datatable-events.md)  
 <span data-ttu-id="6f726-130">Sütun değerleri değiştirildiğinde ve satırlar eklendiğinde veya silindiğinde olaylar da dahil olmak üzere, bir **DataTable**ile kullanılabilecek olaylar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-130">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f726-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6f726-131">Related Sections</span></span>  

 [<span data-ttu-id="6f726-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6f726-132">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="6f726-133">ADO.NET mimarisini ve bileşenlerini ve bunların mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6f726-133">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="6f726-134">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="6f726-134">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="6f726-135">Tablolar arasında ilişki oluşturma dahil olmak üzere ADO.NET **veri kümesi** hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-135">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="6f726-136">**Kısıtlama** nesnesi hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-136">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="6f726-137">**DataColumn** nesnesi hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-137">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="6f726-138">**DataSet** nesnesi hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-138">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="6f726-139">**DataTable** nesnesi hakkında başvuru bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-139">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="6f726-140">Sınıf kitaplığına genel bakış</span><span class="sxs-lookup"><span data-stu-id="6f726-140">Class Library Overview</span></span>](../../../../standard/class-library-overview.md)  
 <span data-ttu-id="6f726-141">**Sistem** ad alanı ve **System. Data**dahil olmak üzere, .NET Framework sınıf kitaplığına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f726-141">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f726-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f726-142">See also</span></span>

- [<span data-ttu-id="6f726-143">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f726-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
