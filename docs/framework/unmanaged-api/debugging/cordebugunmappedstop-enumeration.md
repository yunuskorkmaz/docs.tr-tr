---
description: 'Daha fazla bilgi edinin: CorDebugUnmappedStop numaralandırması'
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
ms.openlocfilehash: 9c4f70c5de451689f98a1c08627fd6df5128fdbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801533"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="7ff59-103">CorDebugUnmappedStop Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7ff59-103">CorDebugUnmappedStop Enumeration</span></span>

<span data-ttu-id="7ff59-104">Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ff59-104">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff59-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ff59-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7ff59-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ff59-106">Members</span></span>  
  
|<span data-ttu-id="7ff59-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7ff59-107">Member</span></span>|<span data-ttu-id="7ff59-108">Description</span><span class="sxs-lookup"><span data-stu-id="7ff59-108">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="7ff59-109">Herhangi bir eşlenmemiş kod türünde durmayın.</span><span class="sxs-lookup"><span data-stu-id="7ff59-109">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="7ff59-110">Giriş kodunda durdur.</span><span class="sxs-lookup"><span data-stu-id="7ff59-110">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="7ff59-111">Bitiş kodunda durdur.</span><span class="sxs-lookup"><span data-stu-id="7ff59-111">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="7ff59-112">Eşleme bilgilerine sahip olmayan kodda durdur.</span><span class="sxs-lookup"><span data-stu-id="7ff59-112">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="7ff59-113">Giriş, bitiş, hiçbir eşleme bilgisi veya yönetilmeyen kategoriye uymayan eşlenmemiş kodda durun.</span><span class="sxs-lookup"><span data-stu-id="7ff59-113">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="7ff59-114">Yönetilmeyen kodda durdur.</span><span class="sxs-lookup"><span data-stu-id="7ff59-114">Stop in unmanaged code.</span></span> <span data-ttu-id="7ff59-115">Bu değer yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ff59-115">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="7ff59-116">Eşlenmemiş kod türlerinde durun.</span><span class="sxs-lookup"><span data-stu-id="7ff59-116">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ff59-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ff59-117">Remarks</span></span>  

 <span data-ttu-id="7ff59-118">Stepper 'in durdurulacağı eşlenmemiş kodu belirten bayrakları ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ff59-118">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff59-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff59-119">Requirements</span></span>  

 <span data-ttu-id="7ff59-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff59-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff59-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ff59-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ff59-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ff59-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ff59-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff59-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff59-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff59-124">See also</span></span>

- [<span data-ttu-id="7ff59-125">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7ff59-125">Debugging Enumerations</span></span>](debugging-enumerations.md)
