---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport Arabirimi'
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
ms.openlocfilehash: bb9c5163e4f5b68700e5a3836fa55edbbebac01c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753646"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="2a433-103">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a433-103">IMetaDataAssemblyImport Interface</span></span>

<span data-ttu-id="2a433-104">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a433-104">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a433-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2a433-105">Methods</span></span>  
  
|<span data-ttu-id="2a433-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a433-106">Method</span></span>|<span data-ttu-id="2a433-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a433-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a433-108">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-108">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="2a433-109">Belirtilen Numaralandırıcı için tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="2a433-109">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="2a433-110">EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-110">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="2a433-111">`mdAssemblyRef`Geçerli meta veri kapsamındaki derlemenin başvurduğu derlemelerin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-111">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="2a433-112">EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-112">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="2a433-113">`mdExportedType`Geçerli meta veri kapsamındaki derlemenin başvurduğu com türlerinin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-113">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="2a433-114">EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-114">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="2a433-115">`mdFile`Geçerli meta veri kapsamındaki derlemenin başvurduğu dosyaların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-115">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="2a433-116">EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-116">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="2a433-117">`mdManifestResource`Geçerli meta veri kapsamındaki derlemenin başvurduğu kaynakların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-117">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="2a433-118">FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-118">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="2a433-119">`mdAssemblyRef`Belirtilen ada sahip derlemeler için bir belirteç dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-119">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="2a433-120">FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-120">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="2a433-121">`mdExportedType`Belirtilen ada sahıp com türü için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-121">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="2a433-122">FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-122">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="2a433-123">`mdManifestResource`Belirtilen ada sahip kaynak için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-123">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="2a433-124">GetAssemblyFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-124">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="2a433-125">Geçerli meta veri kapsamındaki derleme belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-125">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="2a433-126">GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-126">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="2a433-127">Belirtilen derlemenin özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-127">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="2a433-128">GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-128">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="2a433-129">Belirtilen belirtecin özellik ayarlarını alır `mdAssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="2a433-129">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="2a433-130">GetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-130">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="2a433-131">Belirtilen COM türünün özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-131">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="2a433-132">GetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-132">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="2a433-133">Belirtilen dosyanın özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-133">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="2a433-134">GetManifestResourceProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a433-134">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="2a433-135">Belirtilen bildirim kaynağının özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2a433-135">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a433-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a433-136">Requirements</span></span>  

 <span data-ttu-id="2a433-137">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a433-137">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a433-138">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2a433-138">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a433-139">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2a433-139">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a433-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a433-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a433-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a433-141">See also</span></span>

- [<span data-ttu-id="2a433-142">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2a433-142">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="2a433-143">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a433-143">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
