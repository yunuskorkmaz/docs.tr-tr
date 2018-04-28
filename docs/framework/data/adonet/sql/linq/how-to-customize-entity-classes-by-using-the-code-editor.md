---
title: 'Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f57b07d03297347561b6b2e2634038aa1f29bc40
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="cdd61-102">Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cdd61-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="cdd61-103">Visual Studio kullanarak geliştiricileri kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] oluşturmak veya kendi sınıflar özelleştirme.</span><span class="sxs-lookup"><span data-stu-id="cdd61-103">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="cdd61-104">Visual Studio kod düzenleyicisini, kendi eşleme kod yazmaya veya zaten oluşturulmuş kodu özelleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd61-104">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="cdd61-105">Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="cdd61-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="cdd61-106">Bu bölümdeki konular, nesne modeli özelleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="cdd61-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="cdd61-107">Nasıl yapılır: Veritabanı Adları Belirtme</span><span class="sxs-lookup"><span data-stu-id="cdd61-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="cdd61-108">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-109">Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="cdd61-110">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="cdd61-111">Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="cdd61-112">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="cdd61-113">Nasıl yapılır: Birincil Anahtarları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="cdd61-114">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-115">Nasıl yapılır: Veritabanı İlişkilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="cdd61-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="cdd61-116">Kullanım örnekleri sağlar <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cdd61-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="cdd61-117">Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="cdd61-118">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-119">Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="cdd61-120">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-121">Nasıl yapılır: Veritabanı Veri Türleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="cdd61-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="cdd61-122">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-123">Nasıl yapılır: Hesaplanan Sütunları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="cdd61-124">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-125">Nasıl yapılır: Özel Depolama Alanları Belirtme</span><span class="sxs-lookup"><span data-stu-id="cdd61-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="cdd61-126">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-127">Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="cdd61-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="cdd61-128">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="cdd61-129">Nasıl yapılır: Devralma Hiyerarşilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="cdd61-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="cdd61-130">Devralma Hiyerarşisi belirtmek için gerekli eşlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="cdd61-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="cdd61-131">Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme</span><span class="sxs-lookup"><span data-stu-id="cdd61-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="cdd61-132">Nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="cdd61-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd61-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdd61-133">See Also</span></span>  
 [<span data-ttu-id="cdd61-134">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="cdd61-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
