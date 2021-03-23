---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback10:: EventPipeProviderCreated yöntemi'
title: 'ICorProfilerCallback10:: EventPipeProviderCreated yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeProviderCreated
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4602438148a369f2a2321a2ec2e959cc375e37cf
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805590"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a><span data-ttu-id="120b8-103">ICorProfilerCallback10:: EventPipeProviderCreated yöntemi</span><span class="sxs-lookup"><span data-stu-id="120b8-103">ICorProfilerCallback10::EventPipeProviderCreated Method</span></span>

<span data-ttu-id="120b8-104">Bir EventPipe sağlayıcısı oluşturulduğunda profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="120b8-104">Notifies the profiler whenever an EventPipe provider is created.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="120b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="120b8-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider); 
```  
  
## <a name="parameters"></a><span data-ttu-id="120b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="120b8-106">Parameters</span></span>

<span data-ttu-id="120b8-107">`provider` 'ndaki Oluşturulan sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="120b8-107">`provider` [in] The provider that was created.</span></span>

## <a name="requirements"></a><span data-ttu-id="120b8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="120b8-108">Requirements</span></span>  

<span data-ttu-id="120b8-109">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="120b8-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="120b8-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="120b8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="120b8-111">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="120b8-111">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120b8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="120b8-112">See also</span></span>

- [<span data-ttu-id="120b8-113">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="120b8-113">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="120b8-114">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="120b8-114">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="120b8-115">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="120b8-115">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="120b8-116">ICorProfilerInfo12. EventPipeAddProviderToSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="120b8-116">ICorProfilerInfo12.EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
