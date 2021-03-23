---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeStopSession yöntemi'
title: 'ICorProfilerInfo12:: EventPipeStopSession yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeStopSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c1b104f63755bcec52a113be7e2aa9af76ecd34e
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805720"
---
# <a name="icorprofilerinfo12eventpipestopsession-method"></a><span data-ttu-id="32f85-103">ICorProfilerInfo12:: EventPipeStopSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="32f85-103">ICorProfilerInfo12::EventPipeStopSession Method</span></span>

<span data-ttu-id="32f85-104">Bir EventPipe oturumunu durdurup gelecekteki olayların oturuma yazılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="32f85-104">Stops an EventPipe session, preventing any future events from being written to the session.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="32f85-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32f85-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeStopSession(
        [in] EVENTPIPE_SESSION session);
```  
  
## <a name="parameters"></a><span data-ttu-id="32f85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32f85-106">Parameters</span></span>

<span data-ttu-id="32f85-107">`session` 'ndaki Durdurulacak oturumun KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="32f85-107">`session` [in] The ID of the session to stop.</span></span>

## <a name="requirements"></a><span data-ttu-id="32f85-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32f85-108">Requirements</span></span>  

<span data-ttu-id="32f85-109">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="32f85-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="32f85-110">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32f85-110">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="32f85-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32f85-111">See also</span></span>

- [<span data-ttu-id="32f85-112">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="32f85-112">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="32f85-113">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="32f85-113">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="32f85-114">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="32f85-114">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
