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
ms.openlocfilehash: 57d7c3256d7b52a4e55dbb5bc420b0438983d2f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609535"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="0d802-102">COR_DEBUG_STEP_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="0d802-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="0d802-103">Kod aralığı uzaklık bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0d802-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="0d802-104">Bu yapı tarafından kullanılan [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d802-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d802-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d802-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="0d802-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0d802-106">Members</span></span>  
  
|<span data-ttu-id="0d802-107">Üye</span><span class="sxs-lookup"><span data-stu-id="0d802-107">Member</span></span>|<span data-ttu-id="0d802-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d802-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="0d802-109">Aralığın başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="0d802-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="0d802-110">Aralığın uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="0d802-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d802-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d802-111">Requirements</span></span>  
 <span data-ttu-id="0d802-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d802-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d802-113">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="0d802-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="0d802-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d802-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d802-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d802-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d802-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d802-116">See also</span></span>

- [<span data-ttu-id="0d802-117">StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d802-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="0d802-118">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="0d802-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="0d802-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0d802-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
