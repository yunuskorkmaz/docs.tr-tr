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
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436312"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="6715e-102">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6715e-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="6715e-103">Provides methods to access and examine the contents of an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="6715e-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6715e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6715e-104">Methods</span></span>  
  
|<span data-ttu-id="6715e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6715e-105">Method</span></span>|<span data-ttu-id="6715e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6715e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6715e-107">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="6715e-108">Releases the handle to the specified enumerator.</span><span class="sxs-lookup"><span data-stu-id="6715e-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="6715e-109">EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="6715e-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="6715e-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="6715e-111">EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="6715e-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="6715e-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="6715e-113">EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="6715e-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="6715e-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="6715e-115">EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="6715e-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="6715e-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="6715e-117">FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="6715e-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span><span class="sxs-lookup"><span data-stu-id="6715e-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="6715e-119">FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="6715e-120">Gets an `mdExportedType` token for the COM type with the specified name.</span><span class="sxs-lookup"><span data-stu-id="6715e-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="6715e-121">FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="6715e-122">Gets an `mdManifestResource` token for the resource with the specified name.</span><span class="sxs-lookup"><span data-stu-id="6715e-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="6715e-123">GetAssemblyFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="6715e-124">Gets the token for the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="6715e-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="6715e-125">GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="6715e-126">Gets the property settings of the specified assembly.</span><span class="sxs-lookup"><span data-stu-id="6715e-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="6715e-127">GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="6715e-128">Gets the property settings of the specified `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="6715e-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="6715e-129">GetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="6715e-130">Gets the property settings of the specified COM type.</span><span class="sxs-lookup"><span data-stu-id="6715e-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="6715e-131">GetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="6715e-132">Gets the property settings of the specified file.</span><span class="sxs-lookup"><span data-stu-id="6715e-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="6715e-133">GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6715e-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="6715e-134">Gets the property settings of the specified manifest resource.</span><span class="sxs-lookup"><span data-stu-id="6715e-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6715e-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6715e-135">Requirements</span></span>  
 <span data-ttu-id="6715e-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6715e-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6715e-137">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6715e-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6715e-138">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6715e-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6715e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6715e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6715e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6715e-140">See also</span></span>

- [<span data-ttu-id="6715e-141">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6715e-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="6715e-142">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6715e-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
