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
ms.openlocfilehash: 572087bd6f14c43b439910be32fca54af66a2e8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585542"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="53539-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="53539-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="53539-103">Bağlam etkin olup olmadığını belirtir (veya yaprak) çerçevesi yığın üzerinde veya başka bir çerçeveden geriye doğru izleme tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="53539-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53539-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53539-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="53539-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="53539-105">Members</span></span>  
  
|<span data-ttu-id="53539-106">Üye</span><span class="sxs-lookup"><span data-stu-id="53539-106">Member</span></span>|<span data-ttu-id="53539-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53539-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53539-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="53539-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="53539-109">İş parçacığının etkin bağlam bağlamdır.</span><span class="sxs-lookup"><span data-stu-id="53539-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="53539-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="53539-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="53539-111">Bağlamı başka bir çerçeveden geriye doğru izleme hesaplandıktan.</span><span class="sxs-lookup"><span data-stu-id="53539-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53539-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53539-112">Remarks</span></span>  
 <span data-ttu-id="53539-113">`CorDebugSetContextFlag` tarafından kullanılan değerleri sağlar [Icordebugstackwalk::setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53539-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53539-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53539-114">Requirements</span></span>  
 <span data-ttu-id="53539-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53539-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53539-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53539-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53539-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53539-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53539-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53539-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53539-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53539-119">See also</span></span>
- [<span data-ttu-id="53539-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="53539-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="53539-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="53539-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
