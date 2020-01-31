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
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791915"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="cefab-102">ICorDebugRuntimeUnwindableFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cefab-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="cefab-103">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cefab-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cefab-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cefab-104">Remarks</span></span>  
 <span data-ttu-id="cefab-105">`ICorDebugRuntimeUnwindableFrame`, ICorDebugFrame arabiriminin özelleşmiş bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="cefab-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="cefab-106">Çalışma zamanının geçerli yığında bir çerçeveyi geriye doğru bir şekilde aşağı doğru bir şekilde geri kopyasını gerektiren yönetilmeyen yöntemler tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cefab-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="cefab-107">Mevcut geri sarma kuralları, JıT derlenmiş kod kullanmadığından çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cefab-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="cefab-108">Hata ayıklayıcı beklenmeyen bir çerçeve gördüğünde, geri dönmek için [ıcordebugstackizlenecek:: Next](icordebugstackwalk-next-method.md) metodunu kullanmalıdır, ancak İnceleme kendisini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="cefab-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="cefab-109">Hata ayıklayıcı bir `ICorDebugRuntimeUnwindableFrame`aldığında, çerçeve bağlamını almak için [ıcordebugstackyürüme:: GetContext](icordebugstackwalk-getcontext-method.md) metodunu çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="cefab-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cefab-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cefab-110">Requirements</span></span>  
 <span data-ttu-id="cefab-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cefab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cefab-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cefab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cefab-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cefab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cefab-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cefab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefab-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cefab-115">See also</span></span>

- [<span data-ttu-id="cefab-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cefab-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cefab-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cefab-117">Debugging</span></span>](index.md)
