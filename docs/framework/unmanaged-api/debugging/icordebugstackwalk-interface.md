---
title: ICorDebugStackWalk Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
ms.openlocfilehash: 48f1b485b6dfa8fd898f6ea00eee2d7b397deba6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131866"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="5466c-102">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5466c-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="5466c-103">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5466c-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5466c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5466c-104">Methods</span></span>  
  
|<span data-ttu-id="5466c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5466c-105">Method</span></span>|<span data-ttu-id="5466c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5466c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5466c-107">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5466c-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="5466c-108">`ICorDebugStackWalk` nesnesindeki geçerli karenin bağlamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5466c-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="5466c-109">SetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5466c-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="5466c-110">`ICorDebugStackWalk` nesnenin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5466c-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="5466c-111">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5466c-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="5466c-112">`ICorDebugStackWalk` nesnesini sonraki çerçeveye kaydırır.</span><span class="sxs-lookup"><span data-stu-id="5466c-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="5466c-113">GetFrame Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5466c-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="5466c-114">`ICorDebugStackWalk` nesnesindeki geçerli çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="5466c-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5466c-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5466c-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5466c-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="5466c-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5466c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5466c-117">Requirements</span></span>  
 <span data-ttu-id="5466c-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5466c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5466c-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5466c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5466c-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5466c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5466c-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5466c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5466c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5466c-122">See also</span></span>

- [<span data-ttu-id="5466c-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5466c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5466c-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5466c-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
