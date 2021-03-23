---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo12 Interface'
title: ICorProfilerInfo12 arabirimi
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a8b91eba686478c3e825ae15d6ae95bd0ffad944
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805733"
---
# <a name="icorprofilerinfo12-interface"></a><span data-ttu-id="87ffd-103">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ffd-103">ICorProfilerInfo12 Interface</span></span>

 <span data-ttu-id="87ffd-104">EventPipe oturumları, olayları ve sağlayıcıları oluşturmak için yöntemler sağlayan [ICorProfilerInfo11](icorprofilerinfo11-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="87ffd-104">A subclass of [ICorProfilerInfo11](icorprofilerinfo11-interface.md) that provides methods to create EventPipe sessions, events, and providers.</span></span>
  
## <a name="methods"></a><span data-ttu-id="87ffd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="87ffd-105">Methods</span></span>  
  
|<span data-ttu-id="87ffd-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="87ffd-106">Method</span></span>|<span data-ttu-id="87ffd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87ffd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87ffd-108">EventPipeStartSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-108">EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)|<span data-ttu-id="87ffd-109">Profil Oluşturucu EventPipe oturumu başlatır.</span><span class="sxs-lookup"><span data-stu-id="87ffd-109">Starts a profiler EventPipe session.</span></span>|
|[<span data-ttu-id="87ffd-110">EventPipeAddProviderToSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-110">EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)|<span data-ttu-id="87ffd-111">Mevcut bir EventPipe oturumuna bir sağlayıcı ekler.</span><span class="sxs-lookup"><span data-stu-id="87ffd-111">Adds a provider to an existing EventPipe session.</span></span>|
|[<span data-ttu-id="87ffd-112">EventPipeStopSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-112">EventPipeStopSession Method</span></span>](icorprofilerinfo12-eventpipestopsession-method.md)|<span data-ttu-id="87ffd-113">Bir EventPipe oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="87ffd-113">Stops an EventPipe session.</span></span>|
|[<span data-ttu-id="87ffd-114">EventPipeCreateProvider yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-114">EventPipeCreateProvider Method</span></span>](icorprofilerinfo12-eventpipecreateprovider-method.md)|<span data-ttu-id="87ffd-115">Bir EventPipe sağlayıcısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87ffd-115">Creates an EventPipe provider.</span></span>|  
|[<span data-ttu-id="87ffd-116">Eventpipegetproviderınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-116">EventPipeGetProviderInfo Method</span></span>](icorprofilerinfo12-eventpipegetproviderinfo-method.md)|<span data-ttu-id="87ffd-117">Bir EventPipe sağlayıcısının adını KIMLIĞINDEN alır.</span><span class="sxs-lookup"><span data-stu-id="87ffd-117">Gets the name of an EventPipe provider from its ID.</span></span>|
|[<span data-ttu-id="87ffd-118">EventPipeDefineEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-118">EventPipeDefineEvent Method</span></span>](icorprofilerinfo12-eventpipedefineevent-method.md)|<span data-ttu-id="87ffd-119">Mevcut bir EventPipe sağlayıcısında bir olayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87ffd-119">Defines an event on an existing EventPipe provider.</span></span>|  
|[<span data-ttu-id="87ffd-120">EventPipeWriteEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ffd-120">EventPipeWriteEvent Method</span></span>](icorprofilerinfo12-eventpipewriteevent-method.md)|<span data-ttu-id="87ffd-121">Bir EventPipe olayı yazar.</span><span class="sxs-lookup"><span data-stu-id="87ffd-121">Writes an EventPipe event.</span></span>|
  
## <a name="requirements"></a><span data-ttu-id="87ffd-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87ffd-122">Requirements</span></span>  

<span data-ttu-id="87ffd-123">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="87ffd-123">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="87ffd-124">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87ffd-124">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="87ffd-125">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ffd-125">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="87ffd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87ffd-126">See also</span></span>

- [<span data-ttu-id="87ffd-127">EventPipe genel bakış</span><span class="sxs-lookup"><span data-stu-id="87ffd-127">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="87ffd-128">İyi bilinen EventProviders</span><span class="sxs-lookup"><span data-stu-id="87ffd-128">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="87ffd-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87ffd-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="87ffd-130">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ffd-130">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
