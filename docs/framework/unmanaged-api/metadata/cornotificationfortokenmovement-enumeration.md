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
ms.openlocfilehash: 96ab659e6ab6cc9601c0e9a1ab511da92905c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448262"
---
# <a name="cornotificationfortokenmovement-enumeration"></a><span data-ttu-id="45e75-102">CorNotificationForTokenMovement Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="45e75-102">CorNotificationForTokenMovement Enumeration</span></span>
<span data-ttu-id="45e75-103">Belirteç eşleme gerçekleştiğinde, meta veri API istemciye gönderilen bildirimleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="45e75-103">Specifies the notifications that will be sent to the metadata API client when a token remap occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45e75-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="45e75-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="45e75-105">Members</span></span>  
  
|<span data-ttu-id="45e75-106">Üye</span><span class="sxs-lookup"><span data-stu-id="45e75-106">Member</span></span>|<span data-ttu-id="45e75-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45e75-107">Description</span></span>|  
|------------|-----------------|  
|`MDNotifyDefault`|<span data-ttu-id="45e75-108">Bildir `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, veya `mdFieldDef` belirteçleri taşıma.</span><span class="sxs-lookup"><span data-stu-id="45e75-108">Notify when `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, or `mdFieldDef` tokens move.</span></span>|  
|`MDNotifyAll`|<span data-ttu-id="45e75-109">Herhangi bir belirteci taşındığında bildirin.</span><span class="sxs-lookup"><span data-stu-id="45e75-109">Notify when any token moves.</span></span>|  
|`MDNotifyNone`|<span data-ttu-id="45e75-110">Belirteçleri taşıdığınızda bildirme.</span><span class="sxs-lookup"><span data-stu-id="45e75-110">Do not notify when tokens move.</span></span>|  
|`MDNotifyMethodDef`|<span data-ttu-id="45e75-111">Bildir bir `mdMethodDef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-111">Notify when an `mdMethodDef` token moves.</span></span>|  
|`MDNotifyMemberRef`|<span data-ttu-id="45e75-112">Bildir bir `mdMemberRef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-112">Notify when an `mdMemberRef` token moves.</span></span>|  
|`MDNotifyFieldDef`|<span data-ttu-id="45e75-113">Bildir bir `mdFieldDef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-113">Notify when an `mdFieldDef` token moves.</span></span>|  
|`MDNotifyTypeRef`|<span data-ttu-id="45e75-114">Bildir bir `mdTypeRef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-114">Notify when an `mdTypeRef` token moves.</span></span>|  
|`MDNotifyTypeDef`|<span data-ttu-id="45e75-115">Bildir bir `mdTypeDef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-115">Notify when an `mdTypeDef` token moves.</span></span>|  
|`MDNotifyParamDef`|<span data-ttu-id="45e75-116">Bildir bir `mdParamDef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-116">Notify when an `mdParamDef` token moves.</span></span>|  
|`MDNotifyInterfaceImpl`|<span data-ttu-id="45e75-117">Bildir bir `mdInterfaceImpl` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-117">Notify when an `mdInterfaceImpl` token moves.</span></span>|  
|`MDNotifyProperty`|<span data-ttu-id="45e75-118">Bildir bir `mdProperty` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-118">Notify when an `mdProperty` token moves.</span></span>|  
|`MDNotifyEvent`|<span data-ttu-id="45e75-119">Bildir bir `mdEvent` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-119">Notify when an `mdEvent` token moves.</span></span>|  
|`MDNotifySignature`|<span data-ttu-id="45e75-120">Bildir bir `mdSignature` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-120">Notify when an `mdSignature` token moves.</span></span>|  
|`MDNotifyTypeSpec`|<span data-ttu-id="45e75-121">Bildir bir `mdTypeSpec` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-121">Notify when an `mdTypeSpec` token moves.</span></span>|  
|`MDNotifyCustomAttribute`|<span data-ttu-id="45e75-122">Bildir bir `mdCustomAttribute` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-122">Notify when an `mdCustomAttribute` token moves.</span></span>|  
|`MDNotifySecurityValue`|<span data-ttu-id="45e75-123">Bildir bir `mdSecurityValue` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-123">Notify when an `mdSecurityValue` token moves.</span></span>|  
|`MDNotifyPermission`|<span data-ttu-id="45e75-124">Bildir bir `mdPermission` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-124">Notify when an `mdPermission` token moves.</span></span>|  
|`MDNotifyModuleRef`|<span data-ttu-id="45e75-125">Bildir bir `mdModuleRef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-125">Notify when an `mdModuleRef` token moves.</span></span>|  
|`MDNotifyNameSpace`|<span data-ttu-id="45e75-126">Bildir bir `mdNameSpace` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-126">Notify when an `mdNameSpace` token moves.</span></span>|  
|`MDNotifyAssemblyRef`|<span data-ttu-id="45e75-127">Bildir bir `mdAssemblyRef` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-127">Notify when an `mdAssemblyRef` token moves.</span></span>|  
|`MDNotifyFile`|<span data-ttu-id="45e75-128">Bildir bir `mdFile` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-128">Notify when an `mdFile` token moves.</span></span>|  
|`MDNotifyExportedType`|<span data-ttu-id="45e75-129">Bildir bir `mdExportedType` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-129">Notify when an `mdExportedType` token moves.</span></span>|  
|`MDNotifyResource`|<span data-ttu-id="45e75-130">Bildir bir `mdManifestResource` belirteci taşır.</span><span class="sxs-lookup"><span data-stu-id="45e75-130">Notify when an `mdManifestResource` token moves.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e75-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45e75-131">Remarks</span></span>  
 <span data-ttu-id="45e75-132">Bir belirteç (yani taşındığı) yeniden eşlenebilir meta veri birleştirme sırasında.</span><span class="sxs-lookup"><span data-stu-id="45e75-132">A token may be re-mapped (that is, moved) during a metadata merge.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e75-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45e75-133">Requirements</span></span>  
 <span data-ttu-id="45e75-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e75-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e75-135">**Başlık:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="45e75-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="45e75-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e75-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e75-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45e75-137">See Also</span></span>  
 [<span data-ttu-id="45e75-138">Meta Veri Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="45e75-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
