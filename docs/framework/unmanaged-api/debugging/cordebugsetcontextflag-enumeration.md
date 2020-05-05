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
ms.openlocfilehash: a3214fc4e52918716f183720c7c616b1fff74bdb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795683"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="7e3da-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7e3da-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="7e3da-103">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e3da-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e3da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e3da-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="7e3da-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7e3da-105">Members</span></span>  
  
|<span data-ttu-id="7e3da-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7e3da-106">Member</span></span>|<span data-ttu-id="7e3da-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e3da-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7e3da-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="7e3da-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="7e3da-109">Bağlam, iş parçacığının etkin bağlamıdır.</span><span class="sxs-lookup"><span data-stu-id="7e3da-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="7e3da-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="7e3da-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="7e3da-111">Bağlam, başka bir çerçeveden geriye doğru geri sarım tarafından hesaplandı.</span><span class="sxs-lookup"><span data-stu-id="7e3da-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e3da-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e3da-112">Remarks</span></span>  
 <span data-ttu-id="7e3da-113">`CorDebugSetContextFlag`[ıcordebugstackyürüme:: SetContext](icordebugstackwalk-setcontext-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e3da-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e3da-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e3da-114">Requirements</span></span>  
 <span data-ttu-id="7e3da-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e3da-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e3da-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e3da-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e3da-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e3da-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e3da-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e3da-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3da-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e3da-119">See also</span></span>

- [<span data-ttu-id="7e3da-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7e3da-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="7e3da-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7e3da-121">Debugging</span></span>](index.md)
