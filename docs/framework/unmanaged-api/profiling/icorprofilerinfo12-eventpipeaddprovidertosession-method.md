---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeAddProviderToSession yöntemi'
title: 'ICorProfilerInfo12:: EventPipeAddProviderToSession yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeAddProviderToSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 70654660c496211c20459ef9ba37dfbd96b829b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805694"
---
# <a name="icorprofilerinfo12eventpipeaddprovidertosession-method"></a><span data-ttu-id="5b9ff-103">ICorProfilerInfo12:: EventPipeAddProviderToSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b9ff-103">ICorProfilerInfo12::EventPipeAddProviderToSession Method</span></span>

<span data-ttu-id="5b9ff-104">Mevcut bir EventPipe oturumuna bir sağlayıcı ekler.</span><span class="sxs-lookup"><span data-stu-id="5b9ff-104">Adds a provider to an existing EventPipe session.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="5b9ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b9ff-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeAddProviderToSession(
        [in] EVENTPIPE_SESSION                 session,
        [in] COR_PRF_EVENTPIPE_PROVIDER_CONFIG providerConfig);
```  
  
## <a name="parameters"></a><span data-ttu-id="5b9ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b9ff-106">Parameters</span></span>

<span data-ttu-id="5b9ff-107">`session` 'ndaki Sağlayıcının ekleneceği oturumun KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5b9ff-107">`session` [in] The ID of the session to add the provider to.</span></span>

<span data-ttu-id="5b9ff-108">`providerConfig` 'ndaki `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` Oturuma eklenecek sağlayıcıyı açıklayan bir sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="5b9ff-108">`providerConfig` [in] A `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` describing the provider to add to the session.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b9ff-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b9ff-109">Requirements</span></span>  

<span data-ttu-id="5b9ff-110">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="5b9ff-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="5b9ff-111">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b9ff-111">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5b9ff-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b9ff-112">See also</span></span>

- [<span data-ttu-id="5b9ff-113">EventPipe genel bakış</span><span class="sxs-lookup"><span data-stu-id="5b9ff-113">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="5b9ff-114">İyi bilinen EventProviders</span><span class="sxs-lookup"><span data-stu-id="5b9ff-114">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="5b9ff-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5b9ff-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5b9ff-116">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b9ff-116">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="5b9ff-117">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b9ff-117">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="5b9ff-118">COR_PRF_EVENTPIPE_PROVIDER_CONFIG yapısı</span><span class="sxs-lookup"><span data-stu-id="5b9ff-118">COR_PRF_EVENTPIPE_PROVIDER_CONFIG Structure</span></span>](cor-prf-eventpipe-provider-config-structure.md)
