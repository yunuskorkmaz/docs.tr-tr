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
ms.openlocfilehash: 07e2ebe8afe6002dee6c45f56fa1f11a4083d6bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145606"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="83ecf-102">ICorProfilerCallback::RuntimeSuspendFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83ecf-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="83ecf-103">Profil Oluşturucu çalışma zamanı, tüm çalışma zamanı iş parçacıkları askıya alınması tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="83ecf-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ecf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83ecf-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="83ecf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83ecf-105">Remarks</span></span>  
 <span data-ttu-id="83ecf-106">Yönetilmeyen kodda olan tüm çalışma zamanı iş parçacığı, çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="83ecf-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="83ecf-107">Çalışma zamanı yeniden devam edene dek bu noktada, ayrıca askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="83ecf-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="83ecf-108">Bu, çalışma zamanı girin yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="83ecf-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="83ecf-109">Tüm çalışma zamanında ya da hemen kesilebilir kodda zaten olduğu ya da bunlar kesilebilir kod ulaştığınızda askıya almak için sorulan askıya akışlardır.</span><span class="sxs-lookup"><span data-stu-id="83ecf-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="83ecf-110">`RuntimeSuspendFinished` Aynı iş parçacığı üzerinde gerçekleşmesi için geri çağırma garantisi [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="83ecf-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83ecf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83ecf-111">Requirements</span></span>  
 <span data-ttu-id="83ecf-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83ecf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83ecf-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83ecf-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83ecf-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83ecf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83ecf-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83ecf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ecf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83ecf-116">See also</span></span>

- [<span data-ttu-id="83ecf-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83ecf-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="83ecf-118">RuntimeSuspendAborted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83ecf-118">RuntimeSuspendAborted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
