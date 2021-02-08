---
description: 'Daha fazla bilgi edinin: Cornotificationfortokentaşıması numaralandırması'
title: CorNotificationForTokenMovement Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 1975598b756499c9c0b017bf7eba9a134af5185f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784320"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="4a483-103">CorNotificationForTokenMovement Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4a483-103">CorNotificationForTokenMovement Enumeration</span></span>

<span data-ttu-id="4a483-104">Belirteç yeniden eşlemesi gerçekleştiğinde meta veri API istemcisine gönderilecek bildirimleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a483-104">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a483-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a483-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a><span data-ttu-id="4a483-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4a483-106">Members</span></span>  
  
|<span data-ttu-id="4a483-107">Üye</span><span class="sxs-lookup"><span data-stu-id="4a483-107">Member</span></span>|<span data-ttu-id="4a483-108">Description</span><span class="sxs-lookup"><span data-stu-id="4a483-108">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="4a483-109">,, `mdTypeRef` `mdMethodDef` `mdMemberRef` Veya `mdFieldDef` belirteçlerin ne zaman taşınacağını bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="4a483-109">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="4a483-110">Herhangi bir belirteç taşınırsa bildir.</span><span class="sxs-lookup"><span data-stu-id="4a483-110">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="4a483-111">Belirteçler taşındığında bildirim vermeyin.</span><span class="sxs-lookup"><span data-stu-id="4a483-111">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="4a483-112">Bir belirteç taşırken bildir `mdMethodDef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-112">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="4a483-113">Bir belirteç taşırken bildir `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-113">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="4a483-114">Bir belirteç taşırken bildir `mdFieldDef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-114">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="4a483-115">Bir belirteç taşırken bildir `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-115">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="4a483-116">Bir belirteç taşırken bildir `mdTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-116">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="4a483-117">Bir belirteç taşırken bildir `mdParamDef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-117">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="4a483-118">Bir belirteç taşırken bildir `mdInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="4a483-118">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="4a483-119">Bir belirteç taşırken bildir `mdProperty` .</span><span class="sxs-lookup"><span data-stu-id="4a483-119">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="4a483-120">Bir belirteç taşırken bildir `mdEvent` .</span><span class="sxs-lookup"><span data-stu-id="4a483-120">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="4a483-121">Bir belirteç taşırken bildir `mdSignature` .</span><span class="sxs-lookup"><span data-stu-id="4a483-121">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="4a483-122">Bir belirteç taşırken bildir `mdTypeSpec` .</span><span class="sxs-lookup"><span data-stu-id="4a483-122">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="4a483-123">Bir belirteç taşırken bildir `mdCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="4a483-123">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="4a483-124">Bir belirteç taşırken bildir `mdSecurityValue` .</span><span class="sxs-lookup"><span data-stu-id="4a483-124">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="4a483-125">Bir belirteç taşırken bildir `mdPermission` .</span><span class="sxs-lookup"><span data-stu-id="4a483-125">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="4a483-126">Bir belirteç taşırken bildir `mdModuleRef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-126">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="4a483-127">Bir belirteç taşırken bildir `mdNameSpace` .</span><span class="sxs-lookup"><span data-stu-id="4a483-127">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="4a483-128">Bir belirteç taşırken bildir `mdAssemblyRef` .</span><span class="sxs-lookup"><span data-stu-id="4a483-128">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="4a483-129">Bir belirteç taşırken bildir `mdFile` .</span><span class="sxs-lookup"><span data-stu-id="4a483-129">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="4a483-130">Bir belirteç taşırken bildir `mdExportedType` .</span><span class="sxs-lookup"><span data-stu-id="4a483-130">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="4a483-131">Bir belirteç taşırken bildir `mdManifestResource` .</span><span class="sxs-lookup"><span data-stu-id="4a483-131">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a483-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a483-132">Remarks</span></span>  

 <span data-ttu-id="4a483-133">Bir belirteç, meta veri birleştirme sırasında yeniden eşlenmiş (yani taşınan) olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a483-133">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a483-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a483-134">Requirements</span></span>  

 <span data-ttu-id="4a483-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a483-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a483-136">**Üst bilgi:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="4a483-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4a483-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a483-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a483-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a483-138">See also</span></span>

- [<span data-ttu-id="4a483-139">Meta Veri Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="4a483-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
