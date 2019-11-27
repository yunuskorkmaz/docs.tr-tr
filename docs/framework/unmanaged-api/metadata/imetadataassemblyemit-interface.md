---
title: IMetaDataAssemblyEmit Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 6b36d63101c1e9550a979d858764e9052cf45792
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447925"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="8a0b6-102">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="8a0b6-103">Kaynakları çözümlemek ve kullanmak için ortak dil çalışma zamanı tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a0b6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a0b6-104">Methods</span></span>  
  
|<span data-ttu-id="8a0b6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a0b6-105">Method</span></span>|<span data-ttu-id="8a0b6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a0b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a0b6-107">DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="8a0b6-108">Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a0b6-109">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="8a0b6-110">Bu derlemenin başvurduğu derleme için meta verileri içeren bir `AssemblyRef` yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a0b6-111">DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="8a0b6-112">Belirtilen içe aktarılmış tür için meta verileri içeren bir `ExportedType` yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a0b6-113">DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="8a0b6-114">Bu derleme tarafından başvurulan derleme için meta verileri içeren bir `File` meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a0b6-115">DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="8a0b6-116">Belirtilen bildirim kaynağı için meta verileri içeren bir `ManifestResource` yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a0b6-117">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="8a0b6-118">Belirtilen `Assembly` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="8a0b6-119">SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="8a0b6-120">Belirtilen `AssemblyRef` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="8a0b6-121">SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="8a0b6-122">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="8a0b6-123">SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="8a0b6-124">Belirtilen `File` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="8a0b6-125">SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="8a0b6-126">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a0b6-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a0b6-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a0b6-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a0b6-128">Requirements</span></span>  
 <span data-ttu-id="8a0b6-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a0b6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a0b6-130">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a0b6-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a0b6-131">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8a0b6-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a0b6-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a0b6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0b6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a0b6-133">See also</span></span>

- [<span data-ttu-id="8a0b6-134">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a0b6-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="8a0b6-135">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a0b6-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
