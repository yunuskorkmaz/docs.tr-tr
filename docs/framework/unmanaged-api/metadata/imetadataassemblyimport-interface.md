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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009021"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="dfb3a-102">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="dfb3a-103">Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfb3a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dfb3a-104">Methods</span></span>  
  
|<span data-ttu-id="dfb3a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dfb3a-105">Method</span></span>|<span data-ttu-id="dfb3a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfb3a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfb3a-107">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="dfb3a-108">Belirtilen Numaralandırıcı için tanıtıcıyı serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="dfb3a-109">EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="dfb3a-110">`mdAssemblyRef`Geçerli meta veri kapsamındaki derlemenin başvurduğu derlemelerin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="dfb3a-111">EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="dfb3a-112">`mdExportedType`Geçerli meta veri kapsamındaki derlemenin başvurduğu com türlerinin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="dfb3a-113">EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="dfb3a-114">`mdFile`Geçerli meta veri kapsamındaki derlemenin başvurduğu dosyaların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="dfb3a-115">EnumManifestResources Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="dfb3a-116">`mdManifestResource`Geçerli meta veri kapsamındaki derlemenin başvurduğu kaynakların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="dfb3a-117">FindAssembliesByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="dfb3a-118">`mdAssemblyRef`Belirtilen ada sahip derlemeler için bir belirteç dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="dfb3a-119">FindExportedTypeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="dfb3a-120">`mdExportedType`Belirtilen ada sahıp com türü için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="dfb3a-121">FindManifestResourceByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="dfb3a-122">`mdManifestResource`Belirtilen ada sahip kaynak için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="dfb3a-123">GetAssemblyFromScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="dfb3a-124">Geçerli meta veri kapsamındaki derleme belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="dfb3a-125">GetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="dfb3a-126">Belirtilen derlemenin özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="dfb3a-127">GetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="dfb3a-128">Belirtilen belirtecin özellik ayarlarını alır `mdAssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="dfb3a-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="dfb3a-129">GetExportedTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="dfb3a-130">Belirtilen COM türünün özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="dfb3a-131">GetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="dfb3a-132">Belirtilen dosyanın özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="dfb3a-133">GetManifestResourceProps Metodu</span><span class="sxs-lookup"><span data-stu-id="dfb3a-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="dfb3a-134">Belirtilen bildirim kaynağının özellik ayarlarını alır.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfb3a-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfb3a-135">Requirements</span></span>  
 <span data-ttu-id="dfb3a-136">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfb3a-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfb3a-137">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dfb3a-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfb3a-138">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dfb3a-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dfb3a-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfb3a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb3a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfb3a-140">See also</span></span>

- [<span data-ttu-id="dfb3a-141">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dfb3a-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="dfb3a-142">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfb3a-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
