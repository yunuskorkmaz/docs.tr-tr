---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeWriteEvent yöntemi'
title: 'ICorProfilerInfo12:: EventPipeWriteEvent yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeWriteEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a0a06ff0fa1c936518586834f4dfc73810ef0e44
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805746"
---
# <a name="icorprofilerinfo12eventpipewriteevent-method"></a><span data-ttu-id="52398-103">ICorProfilerInfo12:: EventPipeWriteEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="52398-103">ICorProfilerInfo12::EventPipeWriteEvent Method</span></span>

<span data-ttu-id="52398-104">Bu olayı etkinleştiren tüm dinleyicilerine bir EventPipe olayı yazar.</span><span class="sxs-lookup"><span data-stu-id="52398-104">Writes an EventPipe event to any listeners who have enabled this event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="52398-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52398-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeWriteEvent(
                [in] EVENTPIPE_EVENT    event,
                [in] UINT32             cData,
                [in, size_is(cData)]
                     COR_PRF_EVENT_DATA data[],
                [in] LPCGUID            pActivityId,
                [in] LPCGUID            pRelatedActivityId);
```  
  
## <a name="parameters"></a><span data-ttu-id="52398-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52398-106">Parameters</span></span>

<span data-ttu-id="52398-107">`event` 'ndaki Yazılmakta olan olayın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="52398-107">`event` [in] The ID of the event being written.</span></span>

<span data-ttu-id="52398-108">`cData` 'ndaki İçindeki öğe sayısı `data` .</span><span class="sxs-lookup"><span data-stu-id="52398-108">`cData` [in] The number of elements in `data`.</span></span>

<span data-ttu-id="52398-109">`data` 'ndaki `COR_PRF_EVENT_DATA` Olay bağımsız değişkenlerini içeren bir dizi.</span><span class="sxs-lookup"><span data-stu-id="52398-109">`data` [in] An array of `COR_PRF_EVENT_DATA` containing the event arguments.</span></span>

<span data-ttu-id="52398-110">`pActivityId` 'ndaki Olayın etkinlik KIMLIĞINI belirten bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52398-110">`pActivityId` [in] A pointer to a GUID specifying the event's activity ID.</span></span>

<span data-ttu-id="52398-111">`pRelatedActivityId` 'ndaki Olayın ilgili etkinlik KIMLIĞINI belirten bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52398-111">`pRelatedActivityId` [in] A pointer to a GUID specifying the event's related activity ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="52398-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52398-112">Requirements</span></span>  

<span data-ttu-id="52398-113">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="52398-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="52398-114">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52398-114">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="52398-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52398-115">See also</span></span>

- [<span data-ttu-id="52398-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="52398-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="52398-117">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="52398-117">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="52398-118">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="52398-118">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="52398-119">COR_PRF_EVENT_DATA yapısı</span><span class="sxs-lookup"><span data-stu-id="52398-119">COR_PRF_EVENT_DATA Structure</span></span>](cor-prf-event-data-structure.md)
