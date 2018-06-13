---
title: CorCheckDuplicatesFor Numaralandırması
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cdb1570b682088e92ff7c7a78d84259d02d8512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444509"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="d434a-102">CorCheckDuplicatesFor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d434a-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="d434a-103">Çoğaltmaları denetlenecek meta veri simgesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d434a-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d434a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d434a-104">Syntax</span></span>  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="d434a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d434a-105">Members</span></span>  
  
|<span data-ttu-id="d434a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d434a-106">Member</span></span>|<span data-ttu-id="d434a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d434a-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="d434a-108">Tüm meta veri simgesi çoğaltmaları denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d434a-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="d434a-109">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="d434a-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="d434a-110">Meta veri simgesi çoğaltmaları denetlemez.</span><span class="sxs-lookup"><span data-stu-id="d434a-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="d434a-111">İçin yinelenenleri `mdTypeDef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="d434a-112">İçin yinelenenleri `mdInterfaceImpl` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="d434a-113">İçin yinelenenleri `mdMethodDef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="d434a-114">İçin yinelenenleri `mdTypeRef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="d434a-115">İçin yinelenenleri `mdMemberRef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="d434a-116">İçin yinelenenleri `mdCustomAttribute` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="d434a-117">İçin yinelenenleri `mdParamDef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="d434a-118">İçin yinelenenleri `mdPermission` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="d434a-119">İçin yinelenenleri `mdProperty` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="d434a-120">İçin yinelenenleri `mdEvent` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="d434a-121">İçin yinelenenleri `mdFieldDef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="d434a-122">İçin yinelenenleri `mdSignature` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="d434a-123">İçin yinelenenleri `mdModuleRef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="d434a-124">İçin yinelenenleri `mdTypeSpec` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="d434a-125">İçin yinelenenleri `mdImplMap` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="d434a-126">İçin yinelenenleri `mdAssemblyRef` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="d434a-127">İçin yinelenenleri `mdFile` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="d434a-128">İçin yinelenenleri `mdExportedType` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="d434a-129">İçin yinelenenleri `mdManifestResource` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="d434a-130">İçin yinelenenleri `mdGenericParam` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="d434a-131">İçin yinelenenleri `mdMethodSpec` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="d434a-132">İçin yinelenenleri `mdGenericParamConstraint` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="d434a-133">İçin yinelenenleri `mdAssembly` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="d434a-134">İçin yinelenenleri `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, ve `mdMethodSpec` belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="d434a-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d434a-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d434a-135">Requirements</span></span>  
 <span data-ttu-id="d434a-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d434a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d434a-137">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d434a-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d434a-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d434a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d434a-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d434a-139">See Also</span></span>  
 [<span data-ttu-id="d434a-140">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d434a-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
