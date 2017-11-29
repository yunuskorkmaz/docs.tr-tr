---
title: "Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d5586e28e784c43488245db814abf32d863232fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="cd18e-102">Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cd18e-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="cd18e-103">Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] kullanabilirsiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] oluşturmak veya kendi sınıflar özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="cd18e-103">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="cd18e-104">Aynı zamanda [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] Kod düzenleyicisinde kendi eşleme kod yazmaya veya zaten oluşturulmuş kodu özelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="cd18e-104">You can also use the [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="cd18e-105">Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="cd18e-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="cd18e-106">Bu bölümdeki konular, nesne modeli özelleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd18e-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="cd18e-107">Nasıl yapılır: veritabanı adları belirtin</span><span class="sxs-lookup"><span data-stu-id="cd18e-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="cd18e-108">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-109">Nasıl yapılır: temsil eden sınıflar olarak tabloları</span><span class="sxs-lookup"><span data-stu-id="cd18e-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="cd18e-110">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="cd18e-111">Nasıl yapılır: sütun sınıf üyeleri olarak temsil eder</span><span class="sxs-lookup"><span data-stu-id="cd18e-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="cd18e-112">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="cd18e-113">Nasıl yapılır: birincil anahtarlar temsil eder</span><span class="sxs-lookup"><span data-stu-id="cd18e-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="cd18e-114">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-115">Nasıl yapılır: veritabanı ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="cd18e-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="cd18e-116">Kullanım örnekleri sağlar <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cd18e-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="cd18e-117">Nasıl yapılır: sütunlar veritabanında oluşturulan olarak temsil eder</span><span class="sxs-lookup"><span data-stu-id="cd18e-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="cd18e-118">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-119">Nasıl yapılır: zaman damgası veya sürümü sütunları sütunları temsil eder</span><span class="sxs-lookup"><span data-stu-id="cd18e-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="cd18e-120">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-121">Nasıl yapılır: veritabanı veri türlerini belirtme</span><span class="sxs-lookup"><span data-stu-id="cd18e-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="cd18e-122">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-123">Nasıl yapılır: hesaplanan sütunlar temsil eder</span><span class="sxs-lookup"><span data-stu-id="cd18e-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="cd18e-124">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-125">Nasıl yapılır: özel depolama alanları belirtin</span><span class="sxs-lookup"><span data-stu-id="cd18e-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="cd18e-126">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-127">Nasıl yapılır: sütun Null değerlere izin veren olarak temsil eder</span><span class="sxs-lookup"><span data-stu-id="cd18e-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="cd18e-128">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="cd18e-129">Nasıl yapılır: eşleme devralma hiyerarşileri</span><span class="sxs-lookup"><span data-stu-id="cd18e-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="cd18e-130">Devralma Hiyerarşisi belirtmek için gerekli eşlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="cd18e-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="cd18e-131">Nasıl yapılır: eşzamanlılık çakışması denetleniyor belirtin</span><span class="sxs-lookup"><span data-stu-id="cd18e-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="cd18e-132">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="cd18e-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd18e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd18e-133">See Also</span></span>  
 [<span data-ttu-id="cd18e-134">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="cd18e-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
