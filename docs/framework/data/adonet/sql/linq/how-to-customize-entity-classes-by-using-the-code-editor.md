---
title: 'Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme'
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 578e0cbd1f6990a5d41007ad31f4c1c938cd3ebe
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793797"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="e6d63-102">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e6d63-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="e6d63-103">Visual Studio kullanan geliştiriciler, varlık sınıflarını oluşturmak veya özelleştirmek için Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e6d63-103">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="e6d63-104">Visual Studio Code Editor ' i kendi eşleme kodunuzu yazmak veya zaten üretilmiş kodu özelleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6d63-104">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="e6d63-105">Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e6d63-105">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="e6d63-106">Bu bölümdeki konularda, nesne modelinizin nasıl özelleştirileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e6d63-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="e6d63-107">Nasıl yapılır: Veritabanı adlarını belirtin</span><span class="sxs-lookup"><span data-stu-id="e6d63-107">How to: Specify Database Names</span></span>](how-to-specify-database-names.md)  
 <span data-ttu-id="e6d63-108">' Nin nasıl <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-109">Nasıl yapılır: Tabloları sınıf olarak temsil etme</span><span class="sxs-lookup"><span data-stu-id="e6d63-109">How to: Represent Tables as Classes</span></span>](how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="e6d63-110">' Nin nasıl <xref:System.Data.Linq.Mapping.TableAttribute>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="e6d63-111">Nasıl yapılır: Sütunları sınıf üyeleri olarak temsil etme</span><span class="sxs-lookup"><span data-stu-id="e6d63-111">How to: Represent Columns as Class Members</span></span>](how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="e6d63-112">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="e6d63-113">Nasıl yapılır: Birincil anahtarları temsil edin</span><span class="sxs-lookup"><span data-stu-id="e6d63-113">How to: Represent Primary Keys</span></span>](how-to-represent-primary-keys.md)  
 <span data-ttu-id="e6d63-114">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-115">Nasıl yapılır: Veritabanı Ilişkilerini eşleme</span><span class="sxs-lookup"><span data-stu-id="e6d63-115">How to: Map Database Relationships</span></span>](how-to-map-database-relationships.md)  
 <span data-ttu-id="e6d63-116"><xref:System.Data.Linq.Mapping.AssociationAttribute> Özniteliğini kullanma örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="e6d63-117">Nasıl yapılır: Sütunları veritabanı tarafından oluşturulan olarak temsil etme</span><span class="sxs-lookup"><span data-stu-id="e6d63-117">How to: Represent Columns as Database-Generated</span></span>](how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="e6d63-118">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-119">Nasıl yapılır: Sütunları zaman damgası veya sürüm sütunları olarak temsil etme</span><span class="sxs-lookup"><span data-stu-id="e6d63-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="e6d63-120">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-121">Nasıl yapılır: Veritabanı veri türlerini belirtin</span><span class="sxs-lookup"><span data-stu-id="e6d63-121">How to: Specify Database Data Types</span></span>](how-to-specify-database-data-types.md)  
 <span data-ttu-id="e6d63-122">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-123">Nasıl yapılır: Hesaplanan sütunları temsil edin</span><span class="sxs-lookup"><span data-stu-id="e6d63-123">How to: Represent Computed Columns</span></span>](how-to-represent-computed-columns.md)  
 <span data-ttu-id="e6d63-124">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-125">Nasıl yapılır: Özel depolama alanlarını belirt</span><span class="sxs-lookup"><span data-stu-id="e6d63-125">How to: Specify Private Storage Fields</span></span>](how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="e6d63-126">' Nin nasıl <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-127">Nasıl yapılır: Sütunları, null değerlere Izin verecek şekilde temsil edin</span><span class="sxs-lookup"><span data-stu-id="e6d63-127">How to: Represent Columns as Allowing Null Values</span></span>](how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="e6d63-128">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="e6d63-129">Nasıl yapılır: Harita devralma hiyerarşileri</span><span class="sxs-lookup"><span data-stu-id="e6d63-129">How to: Map Inheritance Hierarchies</span></span>](how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="e6d63-130">Devralma hiyerarşisi belirtmek için gereken eşlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="e6d63-131">Nasıl yapılır: Eşzamanlılık çakışması denetimini belirtin</span><span class="sxs-lookup"><span data-stu-id="e6d63-131">How to: Specify Concurrency-Conflict Checking</span></span>](how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="e6d63-132">' Nin nasıl <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e6d63-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d63-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6d63-133">See also</span></span>

- [<span data-ttu-id="e6d63-134">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="e6d63-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
