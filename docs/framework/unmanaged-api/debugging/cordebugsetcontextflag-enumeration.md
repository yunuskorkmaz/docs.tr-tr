---
title: CorDebugSetContextFlag Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: 251c96042e8e56112015fb869176c708322267f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097261"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="8ca43-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="8ca43-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="8ca43-103">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ca43-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="8ca43-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="8ca43-105">Members</span></span>  
  
|<span data-ttu-id="8ca43-106">Üye</span><span class="sxs-lookup"><span data-stu-id="8ca43-106">Member</span></span>|<span data-ttu-id="8ca43-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ca43-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8ca43-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="8ca43-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="8ca43-109">Bağlam, iş parçacığının etkin bağlamıdır.</span><span class="sxs-lookup"><span data-stu-id="8ca43-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="8ca43-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="8ca43-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="8ca43-111">Bağlam, başka bir çerçeveden geriye doğru geri sarım tarafından hesaplandı.</span><span class="sxs-lookup"><span data-stu-id="8ca43-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ca43-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ca43-112">Remarks</span></span>  
 <span data-ttu-id="8ca43-113">`CorDebugSetContextFlag`, [ıcordebugstackyürüme:: SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ca43-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca43-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ca43-114">Requirements</span></span>  
 <span data-ttu-id="8ca43-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca43-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca43-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ca43-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ca43-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8ca43-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ca43-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca43-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca43-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ca43-119">See also</span></span>

- [<span data-ttu-id="8ca43-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8ca43-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="8ca43-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8ca43-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
