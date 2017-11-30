---
title: Meta Veri Arabirimleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638727dae1f0f32e5c92c0da7513719bd11ae8d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-interfaces"></a><span data-ttu-id="b0204-102">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b0204-102">Metadata Interfaces</span></span>
<span data-ttu-id="b0204-103">Bu bölümde .NET Framework türleri, yöntemleri, alanları ve benzeri tarafından kullanıma sunulan meta verilerine erişim sağlayan yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0204-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0204-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b0204-104">In This Section</span></span>  
 [<span data-ttu-id="b0204-105">Iceegen arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="b0204-106">Dinamik kod derleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="b0204-107">Ihostfilter arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="b0204-108">İşleme için meta veri belirteçleri işaretlemek çalışma zamanı ana bilgisayar için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="b0204-109">Imaptoken arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="b0204-110">Alınan ve meta veri imzaları yayılan arasında eşleme özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="b0204-111">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="b0204-112">Ortak dil çalışma zamanı tarafından (CLR) gidermek ve kaynakları kullanmak için kullanılan kendinden açıklama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="b0204-113">Imetadataassemblyımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="b0204-114">Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="b0204-115">Imetadataconverter arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="b0204-116">Tür kitaplıkları kendi meta verileri imzalar için eşleme ve diğerine dönüştürmek için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="b0204-117">Imetadatadispenser arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="b0204-118">`IMetaDataDispenser`Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="b0204-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="b0204-119">Bunun yerine `IMetaDataDispenserEx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0204-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="b0204-120">Imetadatadispenserex arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="b0204-121">Oluşturma veya değiştirme meta veriler için bellek alanlarını eşleme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="b0204-122">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="b0204-123">Oluşturmak, değiştirmek ve şu anda tanımlanmış kapsamda derleme hakkındaki meta verileri depolamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="b0204-124">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="b0204-125">Tanımlama ve yöntemleri oluşturucular ve meta veri imzaları türü parametrelerle değiştirme yöntemleri sağlayan <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0204-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="b0204-126">Imetadataerror arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="b0204-127">Hatalar için derlemeyi meta verileri imza çözümlemesi sırasında raporlama için bir geri dönüş mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="b0204-128">Imetadatafilter arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="b0204-129">İşaretleme ve zaten gerçekleştirilecek eylemler yinelenen önlemek için meta veri simgesi filtreleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="b0204-130">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="b0204-131">İçeri aktarma ve diğer derlemelerden türler düzenleme için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="b0204-132">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="b0204-133">Genişletir `IMetaDataImport` genel türleri ile çalışma yeteneği sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="b0204-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="b0204-134">Imetadataınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="b0204-135">Meta veri eşleme bilgilerini bir disk üzerinde dosyasından belleğe alır bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="b0204-136">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="b0204-137">Depolama ve meta veri bilgileri tablolardaki alınması için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="b0204-138">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="b0204-139">Genişletir `IMetaDataTables` meta veri akışlarını ile çalışmak için yöntemler eklenecek.</span><span class="sxs-lookup"><span data-stu-id="b0204-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="b0204-140">Imetadatavalidate arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0204-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="b0204-141">Meta veri imzaları doğrulama için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0204-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b0204-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b0204-142">Related Sections</span></span>  
 [<span data-ttu-id="b0204-143">Meta veri genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="b0204-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="b0204-144">Meta veri numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b0204-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="b0204-145">Meta veri yapıları</span><span class="sxs-lookup"><span data-stu-id="b0204-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="b0204-146">Meta veri Birleşmeleri</span><span class="sxs-lookup"><span data-stu-id="b0204-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
