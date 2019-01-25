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
ms.openlocfilehash: 45340a26b3351ca03b453fbcdb626de199bd6d19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710371"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="346d3-102">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="346d3-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="346d3-103">Kod aralığı uzaklık bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="346d3-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="346d3-104">Bu yapı tarafından kullanılan [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="346d3-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346d3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="346d3-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="346d3-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="346d3-106">Members</span></span>  
  
|<span data-ttu-id="346d3-107">Üye</span><span class="sxs-lookup"><span data-stu-id="346d3-107">Member</span></span>|<span data-ttu-id="346d3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="346d3-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="346d3-109">Aralığın başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="346d3-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="346d3-110">Aralığın uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="346d3-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="346d3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="346d3-111">Requirements</span></span>  
 <span data-ttu-id="346d3-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="346d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="346d3-113">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="346d3-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="346d3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="346d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="346d3-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="346d3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346d3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="346d3-116">See also</span></span>
- [<span data-ttu-id="346d3-117">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="346d3-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="346d3-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="346d3-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="346d3-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="346d3-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
