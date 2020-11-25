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
ms.openlocfilehash: cd85ba2e6a907ff9546614e02b4da5f45e74b924
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726645"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="38174-102">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="38174-102">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="38174-103">Bir kod aralığı için konum bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="38174-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="38174-104">Bu yapı, [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38174-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38174-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38174-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="38174-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="38174-106">Members</span></span>  
  
|<span data-ttu-id="38174-107">Üye</span><span class="sxs-lookup"><span data-stu-id="38174-107">Member</span></span>|<span data-ttu-id="38174-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38174-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="38174-109">Aralığın başındaki fark.</span><span class="sxs-lookup"><span data-stu-id="38174-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="38174-110">Aralığın sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="38174-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38174-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38174-111">Requirements</span></span>  

 <span data-ttu-id="38174-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38174-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38174-113">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="38174-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="38174-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="38174-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38174-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38174-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38174-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38174-116">See also</span></span>

- [<span data-ttu-id="38174-117">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38174-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="38174-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="38174-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="38174-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="38174-119">Debugging</span></span>](index.md)
