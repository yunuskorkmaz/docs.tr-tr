---
title: IMetaDataAssemblyEmit Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a7e4bd68bfd985b8902ae3b2340773ca77eee10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="078f9-102">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="078f9-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="078f9-103">Ortak dil çalışma zamanı tarafından çözümlemek ve kaynakları kullanmak için kullanılan kendinden açıklama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="078f9-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="078f9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="078f9-104">Methods</span></span>  
  
|<span data-ttu-id="078f9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="078f9-105">Method</span></span>|<span data-ttu-id="078f9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="078f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="078f9-107">DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="078f9-108">Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="078f9-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="078f9-109">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="078f9-110">Oluşturur bir `AssemblyRef` Bu bütünleştirilmiş koduna başvuruyor, derleme için meta verileri içeren yapısını ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="078f9-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="078f9-111">DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="078f9-112">Oluşturur bir `ExportedType` belirtilen türü dışarı ve ilişkili meta veri simgesi döndürür için meta verileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="078f9-113">DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="078f9-114">Oluşturur bir `File` derleme bu derlemesi tarafından başvurulan ve ilişkili meta veri simgesi döndürür için meta verileri içeren meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="078f9-115">DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="078f9-116">Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="078f9-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="078f9-117">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="078f9-118">Belirtilen değiştirir `Assembly` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="078f9-119">SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="078f9-120">Belirtilen değiştirir `AssemblyRef` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="078f9-121">SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="078f9-122">Belirtilen değiştirir `ExportedType` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="078f9-123">SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="078f9-124">Belirtilen değiştirir `File` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="078f9-125">SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="078f9-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="078f9-126">Belirtilen değiştirir `ManifestResource` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="078f9-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="078f9-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="078f9-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="078f9-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="078f9-128">Requirements</span></span>  
 <span data-ttu-id="078f9-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="078f9-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="078f9-130">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="078f9-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="078f9-131">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="078f9-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="078f9-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="078f9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078f9-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="078f9-133">See Also</span></span>  
 [<span data-ttu-id="078f9-134">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="078f9-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="078f9-135">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="078f9-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
