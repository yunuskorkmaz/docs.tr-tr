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
ms.openlocfilehash: 11d5e2eb5e2743fca4876ed09add79be3eba514f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274201"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="62769-102">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="62769-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="62769-103">Bir kod aralığı için konum bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="62769-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="62769-104">Bu yapı, [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62769-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62769-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62769-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="62769-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="62769-106">Members</span></span>  
  
|<span data-ttu-id="62769-107">Üye</span><span class="sxs-lookup"><span data-stu-id="62769-107">Member</span></span>|<span data-ttu-id="62769-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62769-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="62769-109">Aralığın başındaki fark.</span><span class="sxs-lookup"><span data-stu-id="62769-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="62769-110">Aralığın sonundaki fark.</span><span class="sxs-lookup"><span data-stu-id="62769-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62769-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62769-111">Requirements</span></span>  
 <span data-ttu-id="62769-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62769-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62769-113">**Üst bilgi** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="62769-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="62769-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="62769-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62769-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62769-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62769-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62769-116">See also</span></span>

- [<span data-ttu-id="62769-117">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62769-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="62769-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="62769-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="62769-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="62769-119">Debugging</span></span>](index.md)
