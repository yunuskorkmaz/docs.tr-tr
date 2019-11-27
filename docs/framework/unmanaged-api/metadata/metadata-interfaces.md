---
title: Meta Veri Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431592"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="7892d-102">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7892d-102">Metadata Interfaces</span></span>
<span data-ttu-id="7892d-103">Bu bölümde, .NET Framework türler, Yöntemler, alanlar vb. tarafından sunulan meta verilere erişim sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7892d-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7892d-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7892d-104">In This Section</span></span>  
 [<span data-ttu-id="7892d-105">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="7892d-106">Dinamik kod derleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="7892d-107">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="7892d-108">Çalışma zamanı ana bilgisayarı için meta veri belirteçlerini işlemek üzere işaretlemek üzere bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="7892d-109">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="7892d-110">İçeri aktarılan ve verilmiş meta veri imzaları arasında eşleme özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="7892d-111">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="7892d-112">Kaynakları çözümlemek ve tüketmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="7892d-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="7892d-114">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="7892d-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="7892d-116">Tür kitaplıklarını meta veri imzalarına eşlemek ve birinden diğerine dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="7892d-117">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7892d-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="7892d-118">`IMetaDataDispenser` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7892d-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="7892d-119">Bunun yerine `IMetaDataDispenserEx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="7892d-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="7892d-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="7892d-121">Meta veri oluşturmak veya değiştirmek için bellek alanını eşleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="7892d-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="7892d-123">Tanımlı olan kapsamda derleme hakkında meta veriler oluşturma, değiştirme ve depolama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="7892d-124">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="7892d-125"><xref:System.Type?displayProperty=nameWithType>türündeki parametrelerle yöntemlerin ve oluşturucuların meta veri imzalarını tanımlamak ve değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="7892d-126">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="7892d-127">Bir derlemenin meta veri imzasının çözümlenmesi sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="7892d-128">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="7892d-129">Zaten alınmış olan işlemleri önlemek için meta veri belirteçleri işaretlemek ve filtrelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="7892d-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="7892d-131">Diğer derlemelerden türleri içeri ve düzenleme için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="7892d-132">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="7892d-133">Genel türlerle çalışma yeteneğini sağlamak için `IMetaDataImport` genişletir.</span><span class="sxs-lookup"><span data-stu-id="7892d-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="7892d-134">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="7892d-135">Diskteki bir dosyadaki meta verilerin belleğe eşlenmesiyle ilgili bilgileri alan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="7892d-136">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="7892d-137">Tablolarda meta veri bilgilerinin depolanması ve alınması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="7892d-138">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="7892d-139">Meta veri akışlarıyla çalışma yöntemlerini dahil etmek için `IMetaDataTables` genişletir.</span><span class="sxs-lookup"><span data-stu-id="7892d-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="7892d-140">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7892d-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="7892d-141">Meta veri imzalarının doğrulanması için kullanılacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7892d-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7892d-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7892d-142">Related Sections</span></span>  
 [<span data-ttu-id="7892d-143">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7892d-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="7892d-144">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7892d-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="7892d-145">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="7892d-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="7892d-146">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="7892d-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
