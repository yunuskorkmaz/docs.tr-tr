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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443780"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="d8868-102">CorCheckDuplicatesFor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d8868-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="d8868-103">Çoğaltılanların denetlenme meta veri belirteçlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8868-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8868-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8868-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d8868-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="d8868-105">Members</span></span>  
  
|<span data-ttu-id="d8868-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="d8868-106">Member</span></span>|<span data-ttu-id="d8868-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8868-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="d8868-108">Yinelenen öğeler için tüm meta veri belirteçlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="d8868-109">Kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d8868-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="d8868-110">Yinelemeler için meta veri belirteçlerini denetlemeyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="d8868-111">`mdTypeDef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="d8868-112">`mdInterfaceImpl` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="d8868-113">`mdMethodDef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="d8868-114">`mdTypeRef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="d8868-115">`mdMemberRef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="d8868-116">`mdCustomAttribute` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="d8868-117">`mdParamDef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="d8868-118">`mdPermission` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="d8868-119">`mdProperty` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="d8868-120">`mdEvent` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="d8868-121">`mdFieldDef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="d8868-122">`mdSignature` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="d8868-123">`mdModuleRef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="d8868-124">`mdTypeSpec` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="d8868-125">`mdImplMap` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="d8868-126">`mdAssemblyRef` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="d8868-127">`mdFile` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="d8868-128">`mdExportedType` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="d8868-129">`mdManifestResource` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="d8868-130">`mdGenericParam` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="d8868-131">`mdMethodSpec` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="d8868-132">`mdGenericParamConstraint` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="d8868-133">`mdAssembly` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="d8868-134">`mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`ve `mdMethodSpec` belirteçlerinin yinelemelerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d8868-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8868-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8868-135">Requirements</span></span>  
 <span data-ttu-id="d8868-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8868-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8868-137">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d8868-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d8868-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8868-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8868-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8868-139">See also</span></span>

- [<span data-ttu-id="d8868-140">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d8868-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
