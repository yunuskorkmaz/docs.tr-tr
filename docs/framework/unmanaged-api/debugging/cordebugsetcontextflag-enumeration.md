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
ms.openlocfilehash: a443332e4f2b0351e99754fae610af39268bb105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789262"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="4698f-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4698f-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="4698f-103">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4698f-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4698f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4698f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="4698f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4698f-105">Members</span></span>  
  
|<span data-ttu-id="4698f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4698f-106">Member</span></span>|<span data-ttu-id="4698f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4698f-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4698f-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="4698f-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="4698f-109">Bağlam, iş parçacığının etkin bağlamıdır.</span><span class="sxs-lookup"><span data-stu-id="4698f-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="4698f-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="4698f-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="4698f-111">Bağlam, başka bir çerçeveden geriye doğru geri sarım tarafından hesaplandı.</span><span class="sxs-lookup"><span data-stu-id="4698f-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4698f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4698f-112">Remarks</span></span>  
 <span data-ttu-id="4698f-113">`CorDebugSetContextFlag`, [ıcordebugstackyürüme:: SetContext](icordebugstackwalk-setcontext-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4698f-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4698f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4698f-114">Requirements</span></span>  
 <span data-ttu-id="4698f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4698f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4698f-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4698f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4698f-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4698f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4698f-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4698f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4698f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4698f-119">See also</span></span>

- [<span data-ttu-id="4698f-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4698f-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="4698f-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4698f-121">Debugging</span></span>](index.md)
