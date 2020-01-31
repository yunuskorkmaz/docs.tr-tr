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
ms.openlocfilehash: 23e168b0f322a580917c3fcfcb767a7d4d4628f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793879"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="cc700-102">CorDebugUnmappedStop Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cc700-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="cc700-103">Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc700-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc700-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc700-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cc700-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="cc700-105">Members</span></span>  
  
|<span data-ttu-id="cc700-106">Üye</span><span class="sxs-lookup"><span data-stu-id="cc700-106">Member</span></span>|<span data-ttu-id="cc700-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc700-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="cc700-108">Herhangi bir eşlenmemiş kod türünde durmayın.</span><span class="sxs-lookup"><span data-stu-id="cc700-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="cc700-109">Giriş kodunda durdur.</span><span class="sxs-lookup"><span data-stu-id="cc700-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="cc700-110">Bitiş kodunda durdur.</span><span class="sxs-lookup"><span data-stu-id="cc700-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="cc700-111">Eşleme bilgilerine sahip olmayan kodda durdur.</span><span class="sxs-lookup"><span data-stu-id="cc700-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="cc700-112">Giriş, bitiş, hiçbir eşleme bilgisi veya yönetilmeyen kategoriye uymayan eşlenmemiş kodda durun.</span><span class="sxs-lookup"><span data-stu-id="cc700-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="cc700-113">Yönetilmeyen kodda durdur.</span><span class="sxs-lookup"><span data-stu-id="cc700-113">Stop in unmanaged code.</span></span> <span data-ttu-id="cc700-114">Bu değer yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cc700-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="cc700-115">Eşlenmemiş kod türlerinde durun.</span><span class="sxs-lookup"><span data-stu-id="cc700-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc700-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc700-116">Remarks</span></span>  
 <span data-ttu-id="cc700-117">Stepper 'in durdurulacağı eşlenmemiş kodu belirten bayrakları ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc700-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc700-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc700-118">Requirements</span></span>  
 <span data-ttu-id="cc700-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc700-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc700-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc700-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc700-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc700-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc700-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc700-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc700-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc700-123">See also</span></span>

- [<span data-ttu-id="cc700-124">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cc700-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
