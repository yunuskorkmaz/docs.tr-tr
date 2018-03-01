---
title: "COR_DEBUG_STEP_RANGE Yapısı"
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
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27b1b7b26ea788683f9b322306c55a4b3945f342
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="f17a2-102">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="f17a2-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="f17a2-103">Kod bir aralık için uzaklık bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f17a2-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="f17a2-104">Bu yapı tarafından kullanılan [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f17a2-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17a2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f17a2-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="f17a2-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f17a2-106">Members</span></span>  
  
|<span data-ttu-id="f17a2-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f17a2-107">Member</span></span>|<span data-ttu-id="f17a2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f17a2-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="f17a2-109">Aralığın başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f17a2-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="f17a2-110">Aralığın sonu uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f17a2-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f17a2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f17a2-111">Requirements</span></span>  
 <span data-ttu-id="f17a2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f17a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f17a2-113">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="f17a2-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f17a2-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f17a2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f17a2-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f17a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17a2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f17a2-116">See Also</span></span>  
 [<span data-ttu-id="f17a2-117">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f17a2-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="f17a2-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="f17a2-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="f17a2-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f17a2-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
