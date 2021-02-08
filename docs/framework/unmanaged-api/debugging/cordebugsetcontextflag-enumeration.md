---
description: 'Bu konuda daha fazla bilgi edinin: CorDebugSetContextFlag numaralandırması'
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
ms.openlocfilehash: 625f24e516ff462cf3d0e628dfff6c08793807ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801559"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="ebe22-103">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ebe22-103">CorDebugSetContextFlag Enumeration</span></span>

<span data-ttu-id="ebe22-104">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebe22-104">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe22-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ebe22-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="ebe22-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ebe22-106">Members</span></span>  
  
|<span data-ttu-id="ebe22-107">Üye</span><span class="sxs-lookup"><span data-stu-id="ebe22-107">Member</span></span>|<span data-ttu-id="ebe22-108">Description</span><span class="sxs-lookup"><span data-stu-id="ebe22-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ebe22-109">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="ebe22-109">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="ebe22-110">Bağlam, iş parçacığının etkin bağlamıdır.</span><span class="sxs-lookup"><span data-stu-id="ebe22-110">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="ebe22-111">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="ebe22-111">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="ebe22-112">Bağlam, başka bir çerçeveden geriye doğru geri sarım tarafından hesaplandı.</span><span class="sxs-lookup"><span data-stu-id="ebe22-112">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebe22-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebe22-113">Remarks</span></span>  

 <span data-ttu-id="ebe22-114">`CorDebugSetContextFlag`[ıcordebugstackyürüme:: SetContext](icordebugstackwalk-setcontext-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebe22-114">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe22-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebe22-115">Requirements</span></span>  

 <span data-ttu-id="ebe22-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebe22-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebe22-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ebe22-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebe22-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ebe22-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebe22-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebe22-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe22-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebe22-120">See also</span></span>

- [<span data-ttu-id="ebe22-121">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ebe22-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="ebe22-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ebe22-122">Debugging</span></span>](index.md)
