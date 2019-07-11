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
ms.openlocfilehash: e959ce7a77ad6ceb7f2fc848193cbd9fff028279
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739610"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="2c450-102">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2c450-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="2c450-103">Bağlam etkin olup olmadığını belirtir (veya yaprak) çerçevesi yığın üzerinde veya başka bir çerçeveden geriye doğru izleme tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2c450-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c450-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c450-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="2c450-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2c450-105">Members</span></span>  
  
|<span data-ttu-id="2c450-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2c450-106">Member</span></span>|<span data-ttu-id="2c450-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c450-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2c450-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="2c450-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="2c450-109">İş parçacığının etkin bağlam bağlamdır.</span><span class="sxs-lookup"><span data-stu-id="2c450-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="2c450-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="2c450-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="2c450-111">Bağlamı başka bir çerçeveden geriye doğru izleme hesaplandıktan.</span><span class="sxs-lookup"><span data-stu-id="2c450-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c450-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c450-112">Remarks</span></span>  
 <span data-ttu-id="2c450-113">`CorDebugSetContextFlag` tarafından kullanılan değerleri sağlar [Icordebugstackwalk::setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2c450-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c450-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c450-114">Requirements</span></span>  
 <span data-ttu-id="2c450-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c450-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c450-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c450-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c450-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c450-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c450-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c450-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c450-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c450-119">See also</span></span>

- [<span data-ttu-id="2c450-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2c450-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="2c450-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2c450-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
