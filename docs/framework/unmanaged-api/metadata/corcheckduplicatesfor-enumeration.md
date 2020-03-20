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
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176194"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="48207-102">CorCheckDuplicatesFor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="48207-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="48207-103">Yinelenenler için denetlenecek meta veri belirteçlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="48207-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48207-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48207-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="48207-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="48207-105">Members</span></span>  
  
|<span data-ttu-id="48207-106">Üye</span><span class="sxs-lookup"><span data-stu-id="48207-106">Member</span></span>|<span data-ttu-id="48207-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48207-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="48207-108">Yinelenenler için tüm meta veri belirteçlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="48207-109">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="48207-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="48207-110">Yinelenenler için meta veri belirteçlerini denetlemeyin.</span><span class="sxs-lookup"><span data-stu-id="48207-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="48207-111">`mdTypeDef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="48207-112">`mdInterfaceImpl` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="48207-113">`mdMethodDef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="48207-114">`mdTypeRef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="48207-115">`mdMemberRef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="48207-116">`mdCustomAttribute` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="48207-117">`mdParamDef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="48207-118">`mdPermission` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="48207-119">`mdProperty` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="48207-120">`mdEvent` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="48207-121">`mdFieldDef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="48207-122">`mdSignature` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="48207-123">`mdModuleRef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="48207-124">`mdTypeSpec` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="48207-125">`mdImplMap` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="48207-126">`mdAssemblyRef` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="48207-127">`mdFile` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="48207-128">`mdExportedType` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="48207-129">`mdManifestResource` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="48207-130">`mdGenericParam` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="48207-131">`mdMethodSpec` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="48207-132">`mdGenericParamConstraint` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="48207-133">`mdAssembly` Belirteçlerin yinelenenlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="48207-134">`mdMemberRef`, `mdTypeRef`, `mdSignature` `mdTypeSpec`, ve `mdMethodSpec` belirteçlerinin kopyalarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="48207-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48207-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48207-135">Requirements</span></span>  
 <span data-ttu-id="48207-136">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48207-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48207-137">**Üstbilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="48207-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="48207-138">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48207-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48207-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48207-139">See also</span></span>

- [<span data-ttu-id="48207-140">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="48207-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
