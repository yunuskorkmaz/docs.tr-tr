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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008127"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="6e890-102">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e890-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="6e890-103">Kaynakları çözümlemek ve kullanmak için ortak dil çalışma zamanı tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e890-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e890-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e890-104">Methods</span></span>  
  
|<span data-ttu-id="6e890-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e890-105">Method</span></span>|<span data-ttu-id="6e890-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e890-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e890-107">DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="6e890-108">Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e890-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6e890-109">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="6e890-110">`AssemblyRef`Bu derlemenin başvurduğu derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e890-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6e890-111">DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="6e890-112">`ExportedType`Belirtilen içe aktarılmış tür için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e890-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6e890-113">DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="6e890-114">`File`Bu derleme tarafından başvurulan derleme için meta verileri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e890-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6e890-115">DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="6e890-116">`ManifestResource`Belirtilen bildirim kaynağı için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e890-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6e890-117">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="6e890-118">Belirtilen `Assembly` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6e890-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="6e890-119">SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="6e890-120">Belirtilen `AssemblyRef` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6e890-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="6e890-121">SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="6e890-122">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6e890-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="6e890-123">SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="6e890-124">Belirtilen `File` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6e890-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="6e890-125">SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e890-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="6e890-126">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6e890-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e890-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e890-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e890-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e890-128">Requirements</span></span>  
 <span data-ttu-id="6e890-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e890-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e890-130">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6e890-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e890-131">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6e890-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e890-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e890-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e890-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e890-133">See also</span></span>

- [<span data-ttu-id="6e890-134">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e890-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="6e890-135">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e890-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
