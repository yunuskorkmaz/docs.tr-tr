---
title: ICorProfilerCallback::RuntimeSuspendFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6412f31417ead963e987e0c50ad46c78a77d367f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750856"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="fbb26-102">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fbb26-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="fbb26-103">Profil Oluşturucu çalışma zamanı, tüm çalışma zamanı iş parçacıkları askıya alınması tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="fbb26-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fbb26-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fbb26-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbb26-105">Remarks</span></span>  
 <span data-ttu-id="fbb26-106">Yönetilmeyen kodda olan tüm çalışma zamanı iş parçacığı, çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fbb26-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="fbb26-107">Çalışma zamanı yeniden devam edene dek bu noktada, ayrıca askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="fbb26-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="fbb26-108">Bu, çalışma zamanı girin yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fbb26-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="fbb26-109">Tüm çalışma zamanında ya da hemen kesilebilir kodda zaten olduğu ya da bunlar kesilebilir kod ulaştığınızda askıya almak için sorulan askıya akışlardır.</span><span class="sxs-lookup"><span data-stu-id="fbb26-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="fbb26-110">`RuntimeSuspendFinished` Aynı iş parçacığı üzerinde gerçekleşmesi için geri çağırma garantisi [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fbb26-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb26-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fbb26-111">Requirements</span></span>  
 <span data-ttu-id="fbb26-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb26-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb26-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fbb26-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbb26-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbb26-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb26-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb26-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbb26-116">See also</span></span>

- [<span data-ttu-id="fbb26-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fbb26-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="fbb26-118">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fbb26-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
