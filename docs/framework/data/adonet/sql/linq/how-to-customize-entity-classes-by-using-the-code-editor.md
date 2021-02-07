---
description: 'Daha fazla bilgi edinin: nasıl yapılır: kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme'
title: 'Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme'
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 6b4e8b5dcd5cb11095667fe95293a376cc63ade8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738994"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="ec1e3-103">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-103">How to: Customize Entity Classes by Using the Code Editor</span></span>

<span data-ttu-id="ec1e3-104">Visual Studio kullanan geliştiriciler, varlık sınıflarını oluşturmak veya özelleştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ec1e3-104">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="ec1e3-105">Visual Studio Code Editor ' i kendi eşleme kodunuzu yazmak veya zaten üretilmiş kodu özelleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec1e3-105">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="ec1e3-106">Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="ec1e3-106">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="ec1e3-107">Bu bölümdeki konularda, nesne modelinizin nasıl özelleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ec1e3-107">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="ec1e3-108">Nasıl yapılır: Veritabanı Adları Belirtme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-108">How to: Specify Database Names</span></span>](how-to-specify-database-names.md)  
 <span data-ttu-id="ec1e3-109">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-109">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-110">Nasıl yapılır: Tabloları Sınıf Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-110">How to: Represent Tables as Classes</span></span>](how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="ec1e3-111">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.TableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-111">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="ec1e3-112">Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-112">How to: Represent Columns as Class Members</span></span>](how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="ec1e3-113">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-113">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="ec1e3-114">Nasıl yapılır: Birincil Anahtarları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-114">How to: Represent Primary Keys</span></span>](how-to-represent-primary-keys.md)  
 <span data-ttu-id="ec1e3-115">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-115">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-116">Nasıl yapılır: Veritabanı İlişkilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-116">How to: Map Database Relationships</span></span>](how-to-map-database-relationships.md)  
 <span data-ttu-id="ec1e3-117">Özniteliğini kullanma örnekleri sağlar <xref:System.Data.Linq.Mapping.AssociationAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-117">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="ec1e3-118">Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-118">How to: Represent Columns as Database-Generated</span></span>](how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="ec1e3-119">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-119">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-120">Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-120">How to: Represent Columns as Timestamp or Version Columns</span></span>](how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="ec1e3-121">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-121">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-122">Nasıl yapılır: Veritabanı Veri Türleri Belirtme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-122">How to: Specify Database Data Types</span></span>](how-to-specify-database-data-types.md)  
 <span data-ttu-id="ec1e3-123">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-123">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-124">Nasıl yapılır: Hesaplanan Sütunları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-124">How to: Represent Computed Columns</span></span>](how-to-represent-computed-columns.md)  
 <span data-ttu-id="ec1e3-125">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-125">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-126">Nasıl yapılır: Özel Depolama Alanları Belirtme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-126">How to: Specify Private Storage Fields</span></span>](how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="ec1e3-127">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-127">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-128">Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-128">How to: Represent Columns as Allowing Null Values</span></span>](how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="ec1e3-129">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-129">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="ec1e3-130">Nasıl yapılır: Devralma Hiyerarşilerini Eşleme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-130">How to: Map Inheritance Hierarchies</span></span>](how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="ec1e3-131">Devralma hiyerarşisi belirtmek için gereken eşlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ec1e3-131">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="ec1e3-132">Nasıl yapılır: Eşzamanlılık Çakışması Denetimini Belirtme</span><span class="sxs-lookup"><span data-stu-id="ec1e3-132">How to: Specify Concurrency-Conflict Checking</span></span>](how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="ec1e3-133">' Nin nasıl kullanılacağını açıklar <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> .</span><span class="sxs-lookup"><span data-stu-id="ec1e3-133">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1e3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec1e3-134">See also</span></span>

- [<span data-ttu-id="ec1e3-135">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="ec1e3-135">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
