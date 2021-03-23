---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: Eventpipegetproviderınfo yöntemi'
title: 'ICorProfilerInfo12:: Eventpipegetproviderınfo yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeGetProviderInfo
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7bc7ffe1c31e88dc1c65f1670f9bd179e732abfe
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805707"
---
# <a name="icorprofilerinfo12eventpipegetproviderinfo-method"></a><span data-ttu-id="c2f3b-103">ICorProfilerInfo12:: Eventpipegetproviderınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2f3b-103">ICorProfilerInfo12::EventPipeGetProviderInfo Method</span></span>

<span data-ttu-id="c2f3b-104">Profil oluşturucunun, diğer EventPipe dinleyicilerinin alması için olayları yazmak üzere kullanabileceği bir EventPipe sağlayıcısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2f3b-104">Creates an EventPipe provider that the profiler can use to write events for other EventPipe listeners to receive.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c2f3b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2f3b-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeGetProviderInfo(
                [in] EVENTPIPE_PROVIDER provider,
                [in]  ULONG      cchName,
                [out] ULONG      *pcchName,
                [out, annotation("_Out_writes_to_(cchName, *pcchName)")]
                      WCHAR      providerName[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="c2f3b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2f3b-106">Parameters</span></span>

<span data-ttu-id="c2f3b-107">`provider` 'ndaki Adına sağlanacak sağlayıcının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c2f3b-107">`provider` [in] The ID of the provider to provide the name for.</span></span>

<span data-ttu-id="c2f3b-108">`cchName` 'ndaki ' Nin karakter cinsinden boyutu `providerName` .</span><span class="sxs-lookup"><span data-stu-id="c2f3b-108">`cchName` [in] The size, in characters, of `providerName`.</span></span>

<span data-ttu-id="c2f3b-109">`pcchName` dışı Toplam karakter uzunluğuna yönelik bir işaretçi `providerName` .</span><span class="sxs-lookup"><span data-stu-id="c2f3b-109">`pcchName` [out] A pointer to the total character length of `providerName`.</span></span>

<span data-ttu-id="c2f3b-110">`providerName` dışı Çağıran, geniş karakter arabelleği sağladı.</span><span class="sxs-lookup"><span data-stu-id="c2f3b-110">`providerName` [out] A caller provided wide character buffer.</span></span> <span data-ttu-id="c2f3b-111">İşlev, arabelleği döndürdüğünde, sağlayıcının adını içerecektir.</span><span class="sxs-lookup"><span data-stu-id="c2f3b-111">When the function returns the buffer will contain the name of the provider.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2f3b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2f3b-112">Requirements</span></span>  

<span data-ttu-id="c2f3b-113">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c2f3b-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="c2f3b-114">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f3b-114">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c2f3b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f3b-115">See also</span></span>

- [<span data-ttu-id="c2f3b-116">EventPipe genel bakış</span><span class="sxs-lookup"><span data-stu-id="c2f3b-116">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="c2f3b-117">İyi bilinen EventProviders</span><span class="sxs-lookup"><span data-stu-id="c2f3b-117">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="c2f3b-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2f3b-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c2f3b-119">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2f3b-119">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="c2f3b-120">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2f3b-120">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
