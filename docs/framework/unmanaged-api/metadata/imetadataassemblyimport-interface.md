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
ms.openlocfilehash: c556fe247754b363ece0c5dc60750068276ddcc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714763"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="52cfc-102">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52cfc-102">IMetaDataAssemblyImport Interface</span></span>

<span data-ttu-id="52cfc-103">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="52cfc-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52cfc-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="52cfc-104">Methods</span></span>  
  
|<span data-ttu-id="52cfc-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="52cfc-105">Method</span></span>|<span data-ttu-id="52cfc-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52cfc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52cfc-107">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="52cfc-108">Belirtilen Numaralandırıcı için tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="52cfc-109">EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="52cfc-110">`mdAssemblyRef`Geçerli meta veri kapsamındaki derlemenin başvurduğu derlemelerin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="52cfc-111">EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="52cfc-112">`mdExportedType`Geçerli meta veri kapsamındaki derlemenin başvurduğu com türlerinin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="52cfc-113">EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="52cfc-114">`mdFile`Geçerli meta veri kapsamındaki derlemenin başvurduğu dosyaların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="52cfc-115">EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="52cfc-116">`mdManifestResource`Geçerli meta veri kapsamındaki derlemenin başvurduğu kaynakların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="52cfc-117">FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="52cfc-118">`mdAssemblyRef`Belirtilen ada sahip derlemeler için bir belirteç dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="52cfc-119">FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="52cfc-120">`mdExportedType`Belirtilen ada sahıp com türü için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="52cfc-121">FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="52cfc-122">`mdManifestResource`Belirtilen ada sahip kaynak için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="52cfc-123">GetAssemblyFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="52cfc-124">Geçerli meta veri kapsamındaki derleme belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="52cfc-125">GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="52cfc-126">Belirtilen derlemenin özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="52cfc-127">GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="52cfc-128">Belirtilen belirtecin özellik ayarlarını alır `mdAssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="52cfc-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="52cfc-129">GetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="52cfc-130">Belirtilen COM türünün özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="52cfc-131">GetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="52cfc-132">Belirtilen dosyanın özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="52cfc-133">GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cfc-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="52cfc-134">Belirtilen bildirim kaynağının özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="52cfc-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52cfc-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52cfc-135">Requirements</span></span>  

 <span data-ttu-id="52cfc-136">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52cfc-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52cfc-137">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="52cfc-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52cfc-138">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="52cfc-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52cfc-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52cfc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cfc-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52cfc-140">See also</span></span>

- [<span data-ttu-id="52cfc-141">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="52cfc-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="52cfc-142">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52cfc-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
