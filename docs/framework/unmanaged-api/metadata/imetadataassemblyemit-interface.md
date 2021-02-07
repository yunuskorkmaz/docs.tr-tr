---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyEmit arabirimi'
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
ms.openlocfilehash: bcfca4eedc14f2292c40874d86c4984b4c1948f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678217"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="ec94d-103">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec94d-103">IMetaDataAssemblyEmit Interface</span></span>

<span data-ttu-id="ec94d-104">Kaynakları çözümlemek ve kullanmak için ortak dil çalışma zamanı tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec94d-104">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec94d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ec94d-105">Methods</span></span>  
  
|<span data-ttu-id="ec94d-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ec94d-106">Method</span></span>|<span data-ttu-id="ec94d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec94d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec94d-108">DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-108">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="ec94d-109">Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec94d-109">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ec94d-110">DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-110">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="ec94d-111">`AssemblyRef`Bu derlemenin başvurduğu derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec94d-111">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ec94d-112">DefineExportedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-112">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="ec94d-113">`ExportedType`Belirtilen içe aktarılmış tür için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec94d-113">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ec94d-114">DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-114">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="ec94d-115">`File`Bu derleme tarafından başvurulan derleme için meta verileri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec94d-115">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ec94d-116">DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-116">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="ec94d-117">`ManifestResource`Belirtilen bildirim kaynağı için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec94d-117">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="ec94d-118">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-118">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="ec94d-119">Belirtilen `Assembly` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec94d-119">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="ec94d-120">SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-120">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="ec94d-121">Belirtilen `AssemblyRef` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec94d-121">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="ec94d-122">SetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-122">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="ec94d-123">Belirtilen `ExportedType` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec94d-123">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="ec94d-124">SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-124">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="ec94d-125">Belirtilen `File` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec94d-125">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="ec94d-126">SetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec94d-126">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="ec94d-127">Belirtilen `ManifestResource` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ec94d-127">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec94d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec94d-128">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec94d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec94d-129">Requirements</span></span>  

 <span data-ttu-id="ec94d-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec94d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec94d-131">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec94d-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec94d-132">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ec94d-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec94d-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec94d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec94d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec94d-134">See also</span></span>

- [<span data-ttu-id="ec94d-135">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec94d-135">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="ec94d-136">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec94d-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
