---
title: Meta Veri Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 5d9b48df740668797a7c901219401e9ea304a8f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672887"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="77101-102">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="77101-102">Metadata Interfaces</span></span>

<span data-ttu-id="77101-103">Bu bölümde, .NET Framework türler, Yöntemler, alanlar vb. tarafından sunulan meta verilere erişim sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77101-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77101-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="77101-104">In This Section</span></span>  

 [<span data-ttu-id="77101-105">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-105">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="77101-106">Dinamik kod derleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="77101-107">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-107">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="77101-108">Çalışma zamanı ana bilgisayarı için meta veri belirteçlerini işlemek üzere işaretlemek üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="77101-109">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-109">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="77101-110">İçeri aktarılan ve verilmiş meta veri imzaları arasında eşleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="77101-111">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-111">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="77101-112">Kaynakları çözümlemek ve tüketmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="77101-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="77101-114">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="77101-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="77101-116">Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="77101-117">IMetaDataDispenser Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-117">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="77101-118">`IMetaDataDispenser` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="77101-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="77101-119">Bunun yerine `IMetaDataDispenserEx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="77101-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="77101-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="77101-121">Meta veri oluşturmak veya değiştirmek için bellek alanını eşleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="77101-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="77101-123">Tanımlı olan kapsamda derleme hakkında meta veriler oluşturma, değiştirme ve depolama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="77101-124">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="77101-125">Yöntemlerin ve oluşturucuların tür parametreleri ile tanımlanması ve değiştirilmesi için yöntemler sağlar <xref:System.Type?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="77101-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="77101-126">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-126">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="77101-127">Bir derlemenin meta veri imzasının çözümlenmesi sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="77101-128">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-128">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="77101-129">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="77101-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="77101-131">Diğer derlemelerden türleri içeri ve düzenleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="77101-132">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="77101-133">`IMetaDataImport`, Genel türlerle çalışma yeteneği sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="77101-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="77101-134">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-134">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="77101-135">Diskteki bir dosyadaki meta verilerin belleğe eşlenmesiyle ilgili bilgileri alan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="77101-136">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-136">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="77101-137">Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="77101-138">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-138">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="77101-139">`IMetaDataTables`Meta veri akışlarıyla çalışmaya yönelik yöntemleri içerecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="77101-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="77101-140">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77101-140">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="77101-141">Meta veri imzalarının doğrulanması için kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77101-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77101-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="77101-142">Related Sections</span></span>  

 [<span data-ttu-id="77101-143">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="77101-143">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="77101-144">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="77101-144">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="77101-145">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="77101-145">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="77101-146">Meta Veri Birleşmeleri</span><span class="sxs-lookup"><span data-stu-id="77101-146">Metadata Unions</span></span>](metadata-unions.md)
