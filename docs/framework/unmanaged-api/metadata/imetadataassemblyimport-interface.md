---
title: IMetaDataAssemblyImport Arabirimi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 373ff0470e2403f91534df0c0ffe4039dbb0f832
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905417"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="c9906-102">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9906-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="c9906-103">Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9906-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9906-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c9906-104">Methods</span></span>  
  
|<span data-ttu-id="c9906-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c9906-105">Method</span></span>|<span data-ttu-id="c9906-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9906-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9906-107">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="c9906-108">Belirtilen Numaralandırıcı tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c9906-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="c9906-109">EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="c9906-110">Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdAssemblyRef` derleme meta verileri geçerli kapsamda tarafından başvurulan derlemelerin belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="c9906-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c9906-111">EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="c9906-112">Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdExportedType` derleme meta verileri geçerli kapsamda tarafından başvurulan COM türlerinin belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="c9906-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c9906-113">EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="c9906-114">Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdFile` derleme meta verileri geçerli kapsamda tarafından başvurulan tüm dosyaların belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="c9906-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c9906-115">EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="c9906-116">Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdManifestResource` derleme meta verileri geçerli kapsamda tarafından başvurulan bir kaynak belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="c9906-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c9906-117">FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="c9906-118">Bir dizisini alır `mdAssemblyRef` belirtilen ada sahip derlemeler için simgeleri.</span><span class="sxs-lookup"><span data-stu-id="c9906-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="c9906-119">FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="c9906-120">Alır bir `mdExportedType` belirtilen ada sahip bir COM türü için belirteç.</span><span class="sxs-lookup"><span data-stu-id="c9906-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="c9906-121">FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="c9906-122">Alır bir `mdManifestResource` belirtilen ada sahip bir kaynak için belirteç.</span><span class="sxs-lookup"><span data-stu-id="c9906-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="c9906-123">GetAssemblyFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="c9906-124">Belirteç derleme için geçerli bir meta veri kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="c9906-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="c9906-125">GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="c9906-126">Belirtilen derleme özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="c9906-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="c9906-127">GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="c9906-128">Belirtilen özellik ayarları alır `mdAssemblyRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="c9906-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="c9906-129">GetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="c9906-130">Belirtilen COM türünün özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="c9906-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="c9906-131">GetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="c9906-132">Belirtilen dosyanın özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="c9906-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="c9906-133">GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9906-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="c9906-134">Belirtilen bildirim kaynağı özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="c9906-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9906-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9906-135">Requirements</span></span>  
 <span data-ttu-id="c9906-136">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9906-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9906-137">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c9906-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9906-138">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c9906-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9906-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9906-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9906-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9906-140">See also</span></span>

- [<span data-ttu-id="c9906-141">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9906-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="c9906-142">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9906-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
