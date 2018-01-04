---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3803d550fe345c6f485dd204cc119f8a927a3501
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datatables"></a><span data-ttu-id="f0b76-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="f0b76-102">DataTables</span></span>
<span data-ttu-id="f0b76-103">A <xref:System.Data.DataSet> tabloları, ilişkileri ve kısıtlamalar koleksiyonu oluşur.</span><span class="sxs-lookup"><span data-stu-id="f0b76-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="f0b76-104">ADO.NET, <xref:System.Data.DataTable> nesneleri tablolarda belirtmek için kullanılan bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f0b76-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="f0b76-105">A **DataTable** bellek içi ilişkisel veri; bir tablo temsil eden veri yerel olması. Burada yer alıyor, ancak Microsoft SQL Server'ı kullanarak gibi bir veri kaynağından doldurulmuş NET tabanlı uygulama bir **DataAdapter** daha fazla bilgi için bkz: [DataAdapter kümesinden doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .</span><span class="sxs-lookup"><span data-stu-id="f0b76-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="f0b76-106">**DataTable** sınıf üyesi olduğu **System.Data** ad alanı .NET Framework sınıf kitaplığı içinde.</span><span class="sxs-lookup"><span data-stu-id="f0b76-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="f0b76-107">Oluşturma ve kullanma bir **DataTable** bağımsız olarak veya bir üyesi olarak bir **DataSet**, ve **DataTable** nesneler de kullanılabilir diğer .NET Framework nesneleri ile birlikte dahil olmak üzere <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="f0b76-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="f0b76-108">Tablo koleksiyonu erişim bir **DataSet** aracılığıyla **tabloları** özelliği **DataSet** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0b76-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="f0b76-109">Şema veya bir tablonun yapısını sütunlar ve kısıtlamalar ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f0b76-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="f0b76-110">Şemasını tanımlayan bir **DataTable** kullanarak <xref:System.Data.DataColumn> nesneleri yanı <xref:System.Data.ForeignKeyConstraint> ve <xref:System.Data.UniqueConstraint> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f0b76-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="f0b76-111">Bir tablodaki sütun bir veri kaynağındaki sütunları eşlemek, ifadeler hesaplanan değerler içeren, otomatik olarak değerlerine artırın veya birincil anahtar değerlerini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f0b76-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="f0b76-112">Bir şema, ek bir **DataTable** de içerir ve veri sipariş satır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0b76-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="f0b76-113"><xref:System.Data.DataRow> Sınıfı, bir tabloda bulunan gerçek verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0b76-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="f0b76-114">Kullandığınız **DataRow** ve onun özelliklerini ve yöntemlerini almak için değerlendirmek ve bir tablodaki verileri değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="f0b76-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="f0b76-115">Bir satır içindeki verilere erişmek ve değiştikçe **DataRow** nesne hem geçerli ve özgün durumuna korur.</span><span class="sxs-lookup"><span data-stu-id="f0b76-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="f0b76-116">Üst-alt kullanarak tablolar arasında ilişkiler oluşturun veya tablolardaki sütunların ilgili daha fazla.</span><span class="sxs-lookup"><span data-stu-id="f0b76-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="f0b76-117">Arasında bir ilişki Oluştur **DataTable** kullanarak nesneleri bir <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="f0b76-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="f0b76-118">**DataRelation** nesneleri sonra belirli bir satır ilgili alt veya üst satırlarını dönmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0b76-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="f0b76-119">Daha fazla bilgi için bkz: [ekleme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="f0b76-119">For more information, see [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0b76-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f0b76-120">In This Section</span></span>  
 [<span data-ttu-id="f0b76-121">DataTable Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0b76-121">Creating a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 <span data-ttu-id="f0b76-122">Nasıl oluşturulacağını açıklar bir **DataTable** ve ekleyebilmek için bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="f0b76-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="f0b76-123">DataTable Şema Tanımı</span><span class="sxs-lookup"><span data-stu-id="f0b76-123">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="f0b76-124">Oluşturma ve kullanma hakkında bilgi sağlar **DataColumn** nesneleri ve kısıtlamalar.</span><span class="sxs-lookup"><span data-stu-id="f0b76-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="f0b76-125">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f0b76-125">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="f0b76-126">Ekleme, değiştirme ve bir tablodaki verileri silme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0b76-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="f0b76-127">Nasıl kullanılacağı açıklanmaktadır **DataTable** tablosundaki verilerde yapılan değişiklikleri incelemek için olaylar.</span><span class="sxs-lookup"><span data-stu-id="f0b76-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="f0b76-128">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="f0b76-128">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="f0b76-129">İle kullanmak için kullanılabilir olan olaylar hakkında bilgi sağlayan bir **DataTable**, sütun değerlerini değiştirildiğinde ve satır eklenmiş veya silinmiş olaylar dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="f0b76-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0b76-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f0b76-130">Related Sections</span></span>  
 [<span data-ttu-id="f0b76-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f0b76-131">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="f0b76-132">ADO.NET açıklar mimarisi ve bileşenleri ve bunları mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="f0b76-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="f0b76-133">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="f0b76-133">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="f0b76-134">ADO.NET hakkında bilgi sağlar **DataSet** tablolar arasında ilişkiler oluşturmak nasıl dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="f0b76-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="f0b76-135">Hakkında başvuru bilgileri sağlar **kısıtlaması** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0b76-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="f0b76-136">Hakkında başvuru bilgileri sağlar **DataColumn** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0b76-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="f0b76-137">Hakkında başvuru bilgileri sağlar **DataSet** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0b76-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="f0b76-138">Hakkında başvuru bilgileri sağlar **DataTable** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0b76-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="f0b76-139">Sınıf Kitaplığına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f0b76-139">Class Library Overview</span></span>](../../../../../docs/standard/class-library-overview.md)  
 <span data-ttu-id="f0b76-140">.NET Framework sınıf kitaplığı genel bir bakış sağlar dahil olmak üzere **sistem** ad alanı, ikinci düzey ad alanı yanı sıra **System.Data**.</span><span class="sxs-lookup"><span data-stu-id="f0b76-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b76-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0b76-141">See Also</span></span>  
 [<span data-ttu-id="f0b76-142">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f0b76-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
