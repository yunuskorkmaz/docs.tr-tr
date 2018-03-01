---
title: "CorDebugMappingResult Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 924cfec87b99cba9621af02d4e78e72094060ae8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="872c7-102">CorDebugMappingResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="872c7-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="872c7-103">Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="872c7-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="872c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="872c7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="872c7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="872c7-105">Members</span></span>  
  
|<span data-ttu-id="872c7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="872c7-106">Member</span></span>|<span data-ttu-id="872c7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="872c7-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="872c7-108">Yerel kod giriş bölümünde olduğundan, IP değeri 0'dır.</span><span class="sxs-lookup"><span data-stu-id="872c7-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="872c7-109">Yerel kod bir bitiş içinde olduğundan, yönteminin son yönerge adresi IP değeri.</span><span class="sxs-lookup"><span data-stu-id="872c7-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="872c7-110">0 IP değeri için hiçbir eşleme bilgilerini yöntemi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="872c7-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="872c7-111">Geçerli adres yöntemi için eşleme bilgilerini olsa da, Microsoft Ara dili (MSIL) kodu eşlenemez.</span><span class="sxs-lookup"><span data-stu-id="872c7-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="872c7-112">IP değeri 0'dır.</span><span class="sxs-lookup"><span data-stu-id="872c7-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="872c7-113">Tam olarak MSIL koda yöntemi eşler ya da IP değeri doğru biçimde çerçeve, yorumlanan.</span><span class="sxs-lookup"><span data-stu-id="872c7-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="872c7-114">Yöntem başarıyla eşlendi, ancak IP değerini yaklaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="872c7-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="872c7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="872c7-115">Remarks</span></span>  
 <span data-ttu-id="872c7-116">Kullanabileceğiniz [Icordebugılframe::getıp](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) yönerge işaretçisi değeri elde etmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="872c7-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="872c7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="872c7-117">Requirements</span></span>  
 <span data-ttu-id="872c7-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="872c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="872c7-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="872c7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="872c7-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="872c7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="872c7-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="872c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="872c7-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="872c7-122">See Also</span></span>  
 [<span data-ttu-id="872c7-123">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="872c7-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
