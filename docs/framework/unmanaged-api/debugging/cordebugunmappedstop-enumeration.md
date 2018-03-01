---
title: "CorDebugUnmappedStop Numaralandırması"
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
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5700a9a058a349ea70020bafb7d4bed73d1f53f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="ba160-102">CorDebugUnmappedStop Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ba160-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="ba160-103">Kod yürütülmesine durdurmak tarafından Adımlayıcı tetikleyebilir eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba160-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba160-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba160-104">Syntax</span></span>  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="ba160-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ba160-105">Members</span></span>  
  
|<span data-ttu-id="ba160-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ba160-106">Member</span></span>|<span data-ttu-id="ba160-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba160-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="ba160-108">Herhangi bir türde eşlenmemiş kod durdurmaz.</span><span class="sxs-lookup"><span data-stu-id="ba160-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="ba160-109">Giriş kodu durdurun.</span><span class="sxs-lookup"><span data-stu-id="ba160-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="ba160-110">Bitiş kodu durdurun.</span><span class="sxs-lookup"><span data-stu-id="ba160-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="ba160-111">Eşleme bilgi bulunmaz kodda durdurun.</span><span class="sxs-lookup"><span data-stu-id="ba160-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="ba160-112">Giriş, bitiş, Hayır eşleme bilgilerini veya yönetilmeyen kategori uymuyor eşlenmemiş kodda durdurun.</span><span class="sxs-lookup"><span data-stu-id="ba160-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="ba160-113">Yönetilmeyen kod içinde durdurun.</span><span class="sxs-lookup"><span data-stu-id="ba160-113">Stop in unmanaged code.</span></span> <span data-ttu-id="ba160-114">Bu değer yalnızca birlikte çalışma hata ayıklamaya geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="ba160-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="ba160-115">İçindeki tüm türler eşlenmemiş kod durdurun.</span><span class="sxs-lookup"><span data-stu-id="ba160-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba160-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba160-116">Remarks</span></span>  
 <span data-ttu-id="ba160-117">Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) Adımlayıcı durduracak eşlenmemiş kod belirten bayrakları ayarlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ba160-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba160-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba160-118">Requirements</span></span>  
 <span data-ttu-id="ba160-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba160-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba160-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba160-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba160-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba160-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba160-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba160-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba160-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba160-123">See Also</span></span>  
 [<span data-ttu-id="ba160-124">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ba160-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
