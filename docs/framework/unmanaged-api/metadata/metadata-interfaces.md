---
title: Meta Veri Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a704d531b1c49ffe653009e0e90f33b7a126e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451005"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="e7a4c-102">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e7a4c-102">Metadata Interfaces</span></span>
<span data-ttu-id="e7a4c-103">Bu bölümde .NET Framework türleri, yöntemleri, alanları ve benzeri tarafından kullanıma sunulan meta verilerine erişim sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7a4c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e7a4c-104">In This Section</span></span>  
 [<span data-ttu-id="e7a4c-105">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="e7a4c-106">Dinamik kod derleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="e7a4c-107">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="e7a4c-108">İşleme için meta veri belirteçleri işaretlemek çalışma zamanı ana bilgisayar için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="e7a4c-109">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="e7a4c-110">Alınan ve meta veri imzaları yayılan arasında eşleme özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="e7a4c-111">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="e7a4c-112">Ortak dil çalışma zamanı tarafından (CLR) gidermek ve kaynakları kullanmak için kullanılan kendinden açıklama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="e7a4c-113">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="e7a4c-114">Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="e7a4c-115">IMetaDataConverter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="e7a4c-116">Tür kitaplıkları kendi meta verileri imzalar için eşleme ve diğerine dönüştürmek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="e7a4c-117">IMetaDataDispenser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="e7a4c-118">`IMetaDataDispenser` Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="e7a4c-119">Bunun yerine `IMetaDataDispenserEx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="e7a4c-120">IMetaDataDispenserEx Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="e7a4c-121">Oluşturma veya değiştirme meta veriler için bellek alanlarını eşleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="e7a4c-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="e7a4c-123">Oluşturmak, değiştirmek ve şu anda tanımlanmış kapsamda derleme hakkındaki meta verileri depolamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="e7a4c-124">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="e7a4c-125">Tanımlama ve yöntemleri oluşturucular ve meta veri imzaları türü parametrelerle değiştirme yöntemleri sağlayan <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="e7a4c-126">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="e7a4c-127">Hatalar için derlemeyi meta verileri imza çözümlemesi sırasında raporlama için bir geri dönüş mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="e7a4c-128">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="e7a4c-129">İşaretleme ve zaten gerçekleştirilecek eylemler yinelenen önlemek için meta veri simgesi filtreleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="e7a4c-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="e7a4c-131">İçeri aktarma ve diğer derlemelerden türler düzenleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="e7a4c-132">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="e7a4c-133">Genişletir `IMetaDataImport` genel türleri ile çalışma yeteneği sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="e7a4c-134">IMetaDataInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="e7a4c-135">Meta veri eşleme bilgilerini bir disk üzerinde dosyasından belleğe alır bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="e7a4c-136">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="e7a4c-137">Depolama ve meta veri bilgileri tablolardaki alınması için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="e7a4c-138">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="e7a4c-139">Genişletir `IMetaDataTables` meta veri akışlarını ile çalışmak için yöntemler eklenecek.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="e7a4c-140">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a4c-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="e7a4c-141">Meta veri imzaları doğrulama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7a4c-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7a4c-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e7a4c-142">Related Sections</span></span>  
 [<span data-ttu-id="e7a4c-143">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e7a4c-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="e7a4c-144">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e7a4c-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="e7a4c-145">Meta Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="e7a4c-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="e7a4c-146">Meta Veri Birleşimleri</span><span class="sxs-lookup"><span data-stu-id="e7a4c-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
