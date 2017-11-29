---
title: IMetaDataAssemblyImport Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport
helpviewer_keywords: IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ef5b913dc9b1391c63cb123e1f922ca61da6a5bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="59c59-102">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59c59-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="59c59-103">Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="59c59-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59c59-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59c59-104">Methods</span></span>  
  
|<span data-ttu-id="59c59-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="59c59-105">Method</span></span>|<span data-ttu-id="59c59-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59c59-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59c59-107">CloseEnum yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="59c59-108">Belirtilen Numaralandırıcı tanıtıcısını serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="59c59-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="59c59-109">EnumAssemblyRefs yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="59c59-110">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdAssemblyRef` geçerli meta veri kapsamında derlemesi tarafından başvurulan derlemelerin belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="59c59-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="59c59-111">EnumExportedTypes yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="59c59-112">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdExportedType` geçerli meta veri kapsamında derlemesi tarafından başvurulan COM türlerinin belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="59c59-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="59c59-113">EnumFiles yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="59c59-114">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdFile` geçerli meta veri kapsamında derlemesi tarafından başvurulan tüm dosyaların belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="59c59-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="59c59-115">EnumManifestResources yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="59c59-116">Arabirim işaretçisi içeren bir numaralandırıcı alır `mdManifestResource` geçerli meta veri kapsamında derlemesi tarafından başvurulan kaynakların belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="59c59-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="59c59-117">FindAssembliesByName yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="59c59-118">Bir dizi alır `mdAssemblyRef` belirtilen ada sahip derlemeler için belirteç.</span><span class="sxs-lookup"><span data-stu-id="59c59-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="59c59-119">FindExportedTypeByName yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="59c59-120">Alır bir `mdExportedType` COM türü belirtilen adla için belirteç.</span><span class="sxs-lookup"><span data-stu-id="59c59-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="59c59-121">FindManifestResourceByName yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="59c59-122">Alır bir `mdManifestResource` belirtilen ada sahip bir kaynak için belirteç.</span><span class="sxs-lookup"><span data-stu-id="59c59-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="59c59-123">GetAssemblyFromScope yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="59c59-124">Belirteç için derleme geçerli meta veri kapsamdaki alır.</span><span class="sxs-lookup"><span data-stu-id="59c59-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="59c59-125">GetAssemblyProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="59c59-126">Belirtilen derleme özellik ayarları alır.</span><span class="sxs-lookup"><span data-stu-id="59c59-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="59c59-127">GetAssemblyRefProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="59c59-128">Belirtilen özellik ayarları alır `mdAssemblyRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="59c59-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="59c59-129">GetExportedTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="59c59-130">Belirtilen COM türünün özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="59c59-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="59c59-131">GetFileProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="59c59-132">Belirtilen dosya özellik ayarları alır.</span><span class="sxs-lookup"><span data-stu-id="59c59-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="59c59-133">GetManifestResourceProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="59c59-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="59c59-134">Belirtilen bildirim kaynağı özellik ayarları alır.</span><span class="sxs-lookup"><span data-stu-id="59c59-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59c59-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59c59-135">Requirements</span></span>  
 <span data-ttu-id="59c59-136">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59c59-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c59-137">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="59c59-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="59c59-138">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="59c59-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59c59-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c59-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c59-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59c59-140">See Also</span></span>  
 [<span data-ttu-id="59c59-141">Meta veri arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59c59-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="59c59-142">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="59c59-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
