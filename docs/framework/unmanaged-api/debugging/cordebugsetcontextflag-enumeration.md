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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: badd79926e8f039cf6b947dd6655e2cd679e3000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406981"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="f834d-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f834d-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="f834d-103">Bağlam etkin olup olmadığını gösterir (veya yaprak) çerçeve yığında veya başka bir çerçevesinden geriye doğru izleme tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="f834d-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f834d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f834d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="f834d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f834d-105">Members</span></span>  
  
|<span data-ttu-id="f834d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f834d-106">Member</span></span>|<span data-ttu-id="f834d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f834d-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f834d-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="f834d-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="f834d-109">Bağlam iş parçacığının etkin bağlamdır.</span><span class="sxs-lookup"><span data-stu-id="f834d-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="f834d-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="f834d-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="f834d-111">Başka bir çerçevesinden geriye doğru izleme bağlamı hesaplandığı.</span><span class="sxs-lookup"><span data-stu-id="f834d-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f834d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f834d-112">Remarks</span></span>  
 <span data-ttu-id="f834d-113">`CorDebugSetContextFlag` tarafından kullanılan değerleri sağlayan [Icordebugstackwalk::setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f834d-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f834d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f834d-114">Requirements</span></span>  
 <span data-ttu-id="f834d-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f834d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f834d-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f834d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f834d-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f834d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f834d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f834d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f834d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f834d-119">See Also</span></span>  
 [<span data-ttu-id="f834d-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f834d-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="f834d-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f834d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
