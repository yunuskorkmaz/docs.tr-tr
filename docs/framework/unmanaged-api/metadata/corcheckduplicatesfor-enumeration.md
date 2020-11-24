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
ms.openlocfilehash: 4acdfd6df410f229a002fa191ef24766748a1262
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672363"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="f109d-102">CorCheckDuplicatesFor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f109d-102">CorCheckDuplicatesFor Enumeration</span></span>

<span data-ttu-id="f109d-103">Çoğaltılanların denetlenme meta veri belirteçlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f109d-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f109d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f109d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="f109d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f109d-105">Members</span></span>  
  
|<span data-ttu-id="f109d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f109d-106">Member</span></span>|<span data-ttu-id="f109d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f109d-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="f109d-108">Yinelenen öğeler için tüm meta veri belirteçlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f109d-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="f109d-109">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="f109d-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="f109d-110">Yinelemeler için meta veri belirteçlerini denetlemeyin.</span><span class="sxs-lookup"><span data-stu-id="f109d-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="f109d-111">Belirteçlerin yinelemelerini denetleyin `mdTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="f109d-112">Belirteçlerin yinelemelerini denetleyin `mdInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="f109d-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="f109d-113">Belirteçlerin yinelemelerini denetleyin `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="f109d-114">Belirteçlerin yinelemelerini denetleyin `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="f109d-115">Belirteçlerin yinelemelerini denetleyin `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="f109d-116">Belirteçlerin yinelemelerini denetleyin `mdCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="f109d-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="f109d-117">Belirteçlerin yinelemelerini denetleyin `mdParamDef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="f109d-118">Belirteçlerin yinelemelerini denetleyin `mdPermission` .</span><span class="sxs-lookup"><span data-stu-id="f109d-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="f109d-119">Belirteçlerin yinelemelerini denetleyin `mdProperty` .</span><span class="sxs-lookup"><span data-stu-id="f109d-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="f109d-120">Belirteçlerin yinelemelerini denetleyin `mdEvent` .</span><span class="sxs-lookup"><span data-stu-id="f109d-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="f109d-121">Belirteçlerin yinelemelerini denetleyin `mdFieldDef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="f109d-122">Belirteçlerin yinelemelerini denetleyin `mdSignature` .</span><span class="sxs-lookup"><span data-stu-id="f109d-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="f109d-123">Belirteçlerin yinelemelerini denetleyin `mdModuleRef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="f109d-124">Belirteçlerin yinelemelerini denetleyin `mdTypeSpec` .</span><span class="sxs-lookup"><span data-stu-id="f109d-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="f109d-125">Belirteçlerin yinelemelerini denetleyin `mdImplMap` .</span><span class="sxs-lookup"><span data-stu-id="f109d-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="f109d-126">Belirteçlerin yinelemelerini denetleyin `mdAssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="f109d-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="f109d-127">Belirteçlerin yinelemelerini denetleyin `mdFile` .</span><span class="sxs-lookup"><span data-stu-id="f109d-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="f109d-128">Belirteçlerin yinelemelerini denetleyin `mdExportedType` .</span><span class="sxs-lookup"><span data-stu-id="f109d-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="f109d-129">Belirteçlerin yinelemelerini denetleyin `mdManifestResource` .</span><span class="sxs-lookup"><span data-stu-id="f109d-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="f109d-130">Belirteçlerin yinelemelerini denetleyin `mdGenericParam` .</span><span class="sxs-lookup"><span data-stu-id="f109d-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="f109d-131">Belirteçlerin yinelemelerini denetleyin `mdMethodSpec` .</span><span class="sxs-lookup"><span data-stu-id="f109d-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="f109d-132">Belirteçlerin yinelemelerini denetleyin `mdGenericParamConstraint` .</span><span class="sxs-lookup"><span data-stu-id="f109d-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="f109d-133">Belirteçlerin yinelemelerini denetleyin `mdAssembly` .</span><span class="sxs-lookup"><span data-stu-id="f109d-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="f109d-134">,,, `mdMemberRef` `mdTypeRef` `mdSignature` `mdTypeSpec` Ve `mdMethodSpec` belirteçlerin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f109d-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f109d-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f109d-135">Requirements</span></span>  

 <span data-ttu-id="f109d-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f109d-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f109d-137">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="f109d-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f109d-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f109d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f109d-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f109d-139">See also</span></span>

- [<span data-ttu-id="f109d-140">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="f109d-140">Metadata Enumerations</span></span>](metadata-enumerations.md)
