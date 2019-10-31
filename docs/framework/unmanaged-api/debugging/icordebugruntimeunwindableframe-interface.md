---
title: ICorDebugRuntimeUnwindableFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131883"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="c94c9-102">ICorDebugRuntimeUnwindableFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c94c9-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="c94c9-103">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c94c9-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c94c9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c94c9-104">Remarks</span></span>  
 <span data-ttu-id="c94c9-105">`ICorDebugRuntimeUnwindableFrame`, ICorDebugFrame arabiriminin özelleşmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="c94c9-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="c94c9-106">Çalışma zamanının geçerli yığında bir çerçeveyi geriye doğru bir şekilde aşağı doğru bir şekilde geri kopyasını gerektiren yönetilmeyen yöntemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c94c9-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="c94c9-107">Mevcut geri sarma kuralları, JıT derlenmiş kod kullanmadığından çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="c94c9-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="c94c9-108">Hata ayıklayıcı beklenmeyen bir çerçeve gördüğünde, geri dönmek için [ıcordebugstackizlenecek:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metodunu kullanmalıdır, ancak İnceleme kendisini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="c94c9-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="c94c9-109">Hata ayıklayıcı bir `ICorDebugRuntimeUnwindableFrame`aldığında, çerçeve bağlamını almak için [ıcordebugstackyürüme:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metodunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="c94c9-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94c9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c94c9-110">Requirements</span></span>  
 <span data-ttu-id="c94c9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c94c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94c9-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c94c9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c94c9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c94c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94c9-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94c9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c94c9-115">See also</span></span>

- [<span data-ttu-id="c94c9-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c94c9-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c94c9-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c94c9-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
