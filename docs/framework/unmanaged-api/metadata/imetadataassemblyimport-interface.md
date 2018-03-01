---
title: IMetaDataAssemblyImport Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 992b588d16bc221f6b72044da40d09fbb6894511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="55322-102">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55322-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="55322-103">Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="55322-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55322-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="55322-104">Methods</span></span>  
  
|<span data-ttu-id="55322-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="55322-105">Method</span></span>|<span data-ttu-id="55322-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55322-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55322-107">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="55322-108">Belirtilen Numaralandırıcı tanıtıcısını serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="55322-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="55322-109">EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="55322-110">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdAssemblyRef` geçerli meta veri kapsamında derlemesi tarafından başvurulan derlemelerin belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="55322-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="55322-111">EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="55322-112">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdExportedType` geçerli meta veri kapsamında derlemesi tarafından başvurulan COM türlerinin belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="55322-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="55322-113">EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="55322-114">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdFile` geçerli meta veri kapsamında derlemesi tarafından başvurulan tüm dosyaların belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="55322-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="55322-115">EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="55322-116">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdManifestResource` geçerli meta veri kapsamında derlemesi tarafından başvurulan kaynakların belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="55322-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="55322-117">FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="55322-118">Bir dizi alır `mdAssemblyRef` belirtilen ada sahip derlemeler için belirteç.</span><span class="sxs-lookup"><span data-stu-id="55322-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="55322-119">FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="55322-120">Alır bir `mdExportedType` COM türü belirtilen adla için belirteç.</span><span class="sxs-lookup"><span data-stu-id="55322-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="55322-121">FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="55322-122">Alır bir `mdManifestResource` belirtilen ada sahip bir kaynak için belirteç.</span><span class="sxs-lookup"><span data-stu-id="55322-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="55322-123">GetAssemblyFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="55322-124">Belirteç için derleme geçerli meta veri kapsamdaki alır.</span><span class="sxs-lookup"><span data-stu-id="55322-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="55322-125">GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="55322-126">Belirtilen derleme özellik ayarları alır.</span><span class="sxs-lookup"><span data-stu-id="55322-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="55322-127">GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="55322-128">Belirtilen özellik ayarları alır `mdAssemblyRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="55322-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="55322-129">GetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="55322-130">Belirtilen COM türünün özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="55322-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="55322-131">GetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="55322-132">Belirtilen dosya özellik ayarları alır.</span><span class="sxs-lookup"><span data-stu-id="55322-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="55322-133">GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55322-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="55322-134">Belirtilen bildirim kaynağı özellik ayarları alır.</span><span class="sxs-lookup"><span data-stu-id="55322-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55322-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55322-135">Requirements</span></span>  
 <span data-ttu-id="55322-136">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55322-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55322-137">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="55322-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55322-138">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="55322-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55322-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55322-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55322-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55322-140">See Also</span></span>  
 [<span data-ttu-id="55322-141">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="55322-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="55322-142">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55322-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
