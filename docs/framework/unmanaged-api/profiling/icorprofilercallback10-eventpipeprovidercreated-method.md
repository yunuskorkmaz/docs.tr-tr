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
ms.openlocfilehash: 6ce96bf301f1c559923df64edd9dd214c28db918
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231316"
---
# <a name="icorprofilercallback10eventpipeprovidercreated-method"></a><span data-ttu-id="4f91b-103">ICorProfilerCallback10:: EventPipeProviderCreated yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f91b-103">ICorProfilerCallback10::EventPipeProviderCreated Method</span></span>

<span data-ttu-id="4f91b-104">Bir EventPipe sağlayıcısı oluşturulduğunda profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="4f91b-104">Notifies the profiler whenever an EventPipe provider is created.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="4f91b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f91b-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeProviderCreated([in] EVENTPIPE_PROVIDER provider);
```  
  
## <a name="parameters"></a><span data-ttu-id="4f91b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f91b-106">Parameters</span></span>

<span data-ttu-id="4f91b-107">`provider` 'ndaki Oluşturulan sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="4f91b-107">`provider` [in] The provider that was created.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f91b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f91b-108">Requirements</span></span>  

<span data-ttu-id="4f91b-109">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="4f91b-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="4f91b-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f91b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="4f91b-111">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f91b-111">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f91b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f91b-112">See also</span></span>

- [<span data-ttu-id="4f91b-113">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f91b-113">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4f91b-114">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f91b-114">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="4f91b-115">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f91b-115">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="4f91b-116">ICorProfilerInfo12. EventPipeAddProviderToSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f91b-116">ICorProfilerInfo12.EventPipeAddProviderToSession Method</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
