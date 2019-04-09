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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6bc73683a6c37ceaaffc635a58803b71c3b6cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134205"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="560a4-102">ICorDebugRuntimeUnwindableFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="560a4-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="560a4-103">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="560a4-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="560a4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="560a4-104">Remarks</span></span>  
 `ICorDebugRuntimeUnwindableFrame` <span data-ttu-id="560a4-105">Icordebugframe arabirimi, özelleştirilmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="560a4-105">is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="560a4-106">Geçerli yığındaki bir çerçeveyi geriye doğru izlemek için çalışma zamanı gerektiren yönetilmeyen yöntemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="560a4-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="560a4-107">JIT olarak derlenmiş kod kullanmadığından mevcut geriye doğru izleme kuralları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="560a4-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="560a4-108">Hata ayıklayıcı izlenemeyen bir çerçeve gördüğünde kullanması gereken [Icordebugstackwalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) yöntemi, ancak geriye doğru izleme, inceleme kendisini gerçekleştirmesi gereken.</span><span class="sxs-lookup"><span data-stu-id="560a4-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="560a4-109">Hata ayıklayıcı aldığında bir `ICorDebugRuntimeUnwindableFrame`, çağırabilirsiniz [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) çerçevenin içeriği almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="560a4-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="560a4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="560a4-110">Requirements</span></span>  
 <span data-ttu-id="560a4-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="560a4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="560a4-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="560a4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="560a4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="560a4-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="560a4-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="560a4-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="560a4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="560a4-115">See also</span></span>

- [<span data-ttu-id="560a4-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="560a4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="560a4-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="560a4-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
