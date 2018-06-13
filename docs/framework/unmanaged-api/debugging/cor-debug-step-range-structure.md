---
title: COR_DEBUG_STEP_RANGE Yapısı
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5809221f2f31bc725c6a62fa5f8f91822f1c157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407248"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="36e2f-102">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="36e2f-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="36e2f-103">Kod bir aralık için uzaklık bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="36e2f-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="36e2f-104">Bu yapı tarafından kullanılan [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36e2f-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e2f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36e2f-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="36e2f-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="36e2f-106">Members</span></span>  
  
|<span data-ttu-id="36e2f-107">Üye</span><span class="sxs-lookup"><span data-stu-id="36e2f-107">Member</span></span>|<span data-ttu-id="36e2f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36e2f-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="36e2f-109">Aralığın başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="36e2f-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="36e2f-110">Aralığın sonu uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="36e2f-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36e2f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36e2f-111">Requirements</span></span>  
 <span data-ttu-id="36e2f-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36e2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36e2f-113">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="36e2f-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="36e2f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36e2f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36e2f-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36e2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e2f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36e2f-116">See Also</span></span>  
 [<span data-ttu-id="36e2f-117">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36e2f-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="36e2f-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="36e2f-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="36e2f-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="36e2f-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
