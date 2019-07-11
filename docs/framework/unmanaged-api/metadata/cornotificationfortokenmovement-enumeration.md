---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a7859bd890a2ecc10b5117f697ff8b06ad569f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781694"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="b0947-102">CorNotificationForTokenMovement Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b0947-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="b0947-103">Belirteç remap gerçekleştiğinde, meta veri API'si istemciye gönderilecek bildirimler belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0947-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0947-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0947-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b0947-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b0947-105">Members</span></span>  
  
|<span data-ttu-id="b0947-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b0947-106">Member</span></span>|<span data-ttu-id="b0947-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0947-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="b0947-108">Bildirim zamanı `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, veya `mdFieldDef` belirteçleri taşıma.</span><span class="sxs-lookup"><span data-stu-id="b0947-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="b0947-109">Herhangi bir belirteci hareket ettiğinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="b0947-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="b0947-110">Belirteçleri taşıdığınızda bildirme.</span><span class="sxs-lookup"><span data-stu-id="b0947-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="b0947-111">Bildirim zamanı bir `mdMethodDef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="b0947-112">Bildirim zamanı bir `mdMemberRef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="b0947-113">Bildirim zamanı bir `mdFieldDef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="b0947-114">Bildirim zamanı bir `mdTypeRef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="b0947-115">Bildirim zamanı bir `mdTypeDef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="b0947-116">Bildirim zamanı bir `mdParamDef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="b0947-117">Bildirim zamanı bir `mdInterfaceImpl` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="b0947-118">Bildirim zamanı bir `mdProperty` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="b0947-119">Bildirim zamanı bir `mdEvent` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="b0947-120">Bildirim zamanı bir `mdSignature` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="b0947-121">Bildirim zamanı bir `mdTypeSpec` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="b0947-122">Bildirim zamanı bir `mdCustomAttribute` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="b0947-123">Bildirim zamanı bir `mdSecurityValue` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="b0947-124">Bildirim zamanı bir `mdPermission` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="b0947-125">Bildirim zamanı bir `mdModuleRef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="b0947-126">Bildirim zamanı bir `mdNameSpace` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="b0947-127">Bildirim zamanı bir `mdAssemblyRef` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="b0947-128">Bildirim zamanı bir `mdFile` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="b0947-129">Bildirim zamanı bir `mdExportedType` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="b0947-130">Bildirim zamanı bir `mdManifestResource` belirteç taşır.</span><span class="sxs-lookup"><span data-stu-id="b0947-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0947-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0947-131">Remarks</span></span>  
 <span data-ttu-id="b0947-132">Bir belirteç (yani taşındı) yeniden eşlenebilir meta veri birleştirme sırasında.</span><span class="sxs-lookup"><span data-stu-id="b0947-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0947-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0947-133">Requirements</span></span>  
 <span data-ttu-id="b0947-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0947-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0947-135">**Üst bilgi:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b0947-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b0947-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0947-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0947-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0947-137">See also</span></span>

- [<span data-ttu-id="b0947-138">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b0947-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
