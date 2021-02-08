---
description: 'Daha fazla bilgi edinin: COR_DEBUG_STEP_RANGE yapısı'
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
ms.openlocfilehash: 40462be4b165351b3265fa0833d19f18e0fa3a37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801845"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="55cb2-103">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="55cb2-103">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="55cb2-104">Bir kod aralığı için konum bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="55cb2-104">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="55cb2-105">Bu yapı, [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55cb2-105">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55cb2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="55cb2-106">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="55cb2-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="55cb2-107">Members</span></span>  
  
|<span data-ttu-id="55cb2-108">Üye</span><span class="sxs-lookup"><span data-stu-id="55cb2-108">Member</span></span>|<span data-ttu-id="55cb2-109">Description</span><span class="sxs-lookup"><span data-stu-id="55cb2-109">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="55cb2-110">Aralığın başındaki fark.</span><span class="sxs-lookup"><span data-stu-id="55cb2-110">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="55cb2-111">Aralığın sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="55cb2-111">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55cb2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55cb2-112">Requirements</span></span>  

 <span data-ttu-id="55cb2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55cb2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55cb2-114">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="55cb2-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="55cb2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="55cb2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55cb2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55cb2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cb2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55cb2-117">See also</span></span>

- [<span data-ttu-id="55cb2-118">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55cb2-118">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="55cb2-119">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="55cb2-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="55cb2-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="55cb2-120">Debugging</span></span>](index.md)
