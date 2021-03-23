---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback10 Interface'
title: ICorProfilerCallback10 arabirimi
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d9091dc81307e2dcb83e74154a8217dffaa1e7a2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805655"
---
# <a name="icorprofilercallback10-interface"></a><span data-ttu-id="c2a90-103">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2a90-103">ICorProfilerCallback10 Interface</span></span>

 <span data-ttu-id="c2a90-104">Profil oluşturucuyu, EventPipe olaylarının Profiler 'ın Şu anda etkin oturumuna teslim edildiğini bildirmek için geri çağırma yöntemleri sağlayan bir [ICorProfilerCallback9](icorprofilercallback9-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2a90-104">A subclass of [ICorProfilerCallback9](icorprofilercallback9-interface.md) that provides callback methods to notify the profiler that EventPipe events have been delivered to the profiler's currently active session.</span></span>
  
## <a name="methods"></a><span data-ttu-id="c2a90-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c2a90-105">Methods</span></span>  
  
|<span data-ttu-id="c2a90-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c2a90-106">Method</span></span>|<span data-ttu-id="c2a90-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2a90-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2a90-108">Eventpipeeventteslim edilen yöntem</span><span class="sxs-lookup"><span data-stu-id="c2a90-108">EventPipeEventDelivered Method</span></span>](icorprofilercallback10-eventpipeeventdelivered-method.md)|<span data-ttu-id="c2a90-109">Profiler öğesine bir EventPipe olayının, profil oluşturucunun açık olduğu oturuma teslim edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c2a90-109">Notifies the profiler that an EventPipe event has been delivered to the session that the profiler has open.</span></span>|
|[<span data-ttu-id="c2a90-110">EventPipeProviderCreated yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2a90-110">EventPipeProviderCreated Method</span></span>](icorprofilercallback10-eventpipeprovidercreated-method.md)|<span data-ttu-id="c2a90-111">Profil oluşturucuya bir EventPipe sağlayıcısının oluşturulduğunu bildirir ve profil oluşturucunun bu sağlayıcıyı oturumlarını eklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2a90-111">Notifies the profiler that an EventPipe provider has been created, allowing the profiler to add that provider the their session.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2a90-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2a90-112">Requirements</span></span>  

<span data-ttu-id="c2a90-113">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c2a90-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="c2a90-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2a90-114">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="c2a90-115">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a90-115">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c2a90-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2a90-116">See also</span></span>

- [<span data-ttu-id="c2a90-117">EventPipe genel bakış</span><span class="sxs-lookup"><span data-stu-id="c2a90-117">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="c2a90-118">İyi bilinen EventProviders</span><span class="sxs-lookup"><span data-stu-id="c2a90-118">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="c2a90-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2a90-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c2a90-120">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2a90-120">ICorProfilerInfo12 Interface</span></span>](ICorProfilerInfo12-interface.md)
- [<span data-ttu-id="c2a90-121">ICorProfilerInfo12. EventPipeStartSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2a90-121">ICorProfilerInfo12.EventPipeStartSession method</span></span>](ICorProfilerInfo12-eventpipestartsession-method.md)
- [<span data-ttu-id="c2a90-122">ICorProfilerInfo12. EventPipeStopSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2a90-122">ICorProfilerInfo12.EventPipeStopSession method</span></span>](ICorProfilerInfo12-eventpipestopsession-method.md)
