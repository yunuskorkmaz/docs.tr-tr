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
ms.openlocfilehash: cc02f63808b1929b93777c8bbc67c47000b0b424
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132742"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="f78c6-102">CorDebugUnmappedStop Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f78c6-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="f78c6-103">Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f78c6-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f78c6-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="f78c6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f78c6-105">Members</span></span>  
  
|<span data-ttu-id="f78c6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f78c6-106">Member</span></span>|<span data-ttu-id="f78c6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f78c6-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="f78c6-108">Herhangi bir eşlenmemiş kod türünde durmayın.</span><span class="sxs-lookup"><span data-stu-id="f78c6-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="f78c6-109">Giriş kodunda durdur.</span><span class="sxs-lookup"><span data-stu-id="f78c6-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="f78c6-110">Bitiş kodunda durdur.</span><span class="sxs-lookup"><span data-stu-id="f78c6-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="f78c6-111">Eşleme bilgilerine sahip olmayan kodda durdur.</span><span class="sxs-lookup"><span data-stu-id="f78c6-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="f78c6-112">Giriş, bitiş, hiçbir eşleme bilgisi veya yönetilmeyen kategoriye uymayan eşlenmemiş kodda durun.</span><span class="sxs-lookup"><span data-stu-id="f78c6-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="f78c6-113">Yönetilmeyen kodda durdur.</span><span class="sxs-lookup"><span data-stu-id="f78c6-113">Stop in unmanaged code.</span></span> <span data-ttu-id="f78c6-114">Bu değer yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f78c6-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="f78c6-115">Eşlenmemiş kod türlerinde durun.</span><span class="sxs-lookup"><span data-stu-id="f78c6-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f78c6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f78c6-116">Remarks</span></span>  
 <span data-ttu-id="f78c6-117">Stepper 'in durdurulacağı eşlenmemiş kodu belirten bayrakları ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f78c6-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f78c6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f78c6-118">Requirements</span></span>  
 <span data-ttu-id="f78c6-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f78c6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f78c6-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f78c6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f78c6-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f78c6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f78c6-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f78c6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f78c6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f78c6-123">See also</span></span>

- [<span data-ttu-id="f78c6-124">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f78c6-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
