---
title: CorDebugUnmappedStop Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f22c045be9af71644415ae3b6b5e64d3e399dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495441"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="21118-102">CorDebugUnmappedStop Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="21118-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="21118-103">Kod yürütülmesine bir durdurmak tarafından adımlayıcıdaki tetikleyebilirsiniz eşlenmemiş kodun türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="21118-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21118-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21118-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="21118-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="21118-105">Members</span></span>  
  
|<span data-ttu-id="21118-106">Üye</span><span class="sxs-lookup"><span data-stu-id="21118-106">Member</span></span>|<span data-ttu-id="21118-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21118-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="21118-108">Herhangi bir türde eşlenmemiş kod durdurmayın.</span><span class="sxs-lookup"><span data-stu-id="21118-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="21118-109">Giriş kodu durdurun.</span><span class="sxs-lookup"><span data-stu-id="21118-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="21118-110">Sonuç kodu durdurun.</span><span class="sxs-lookup"><span data-stu-id="21118-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="21118-111">Eşleme bilgisi kodda durdurun.</span><span class="sxs-lookup"><span data-stu-id="21118-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="21118-112">Giriş, bitiş, Hayır eşleme bilgilerini veya yönetilmeyen bir kategori uymayan eşlenmemiş kodda durdurun.</span><span class="sxs-lookup"><span data-stu-id="21118-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="21118-113">Yönetilmeyen kodda durdurun.</span><span class="sxs-lookup"><span data-stu-id="21118-113">Stop in unmanaged code.</span></span> <span data-ttu-id="21118-114">Bu değer, yalnızca birlikte çalışma hata ayıklama ile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="21118-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="21118-115">Eşlenmemiş kod tüm türlerin durdurun.</span><span class="sxs-lookup"><span data-stu-id="21118-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21118-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21118-116">Remarks</span></span>  
 <span data-ttu-id="21118-117">Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) Adımlayıcı durdurur eşlenmemiş kod belirten bayrakları ayarlamanızı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21118-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21118-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21118-118">Requirements</span></span>  
 <span data-ttu-id="21118-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21118-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21118-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21118-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21118-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21118-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21118-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21118-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21118-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21118-123">See also</span></span>
- [<span data-ttu-id="21118-124">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="21118-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
