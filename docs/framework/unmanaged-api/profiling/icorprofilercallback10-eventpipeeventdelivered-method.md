---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi'
title: 'ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeEventDelivered
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7b2ca813d610c2b41d97d8cd76dac22ca38802d7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805642"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a><span data-ttu-id="b1969-103">ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1969-103">ICorProfilerCallback10::EventPipeEventDelivered Method</span></span>

<span data-ttu-id="b1969-104">Profiler 'ın Şu anda etkin oturumuna her bir EventPipe olayı teslim edildiğinde profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="b1969-104">Notifies the profiler whenever an EventPipe event has been delivered to the profiler's currently active session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1969-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1969-105">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeEventDelivered(
        [in] EVENTPIPE_PROVIDER provider,
        [in] DWORD eventId,
        [in] DWORD eventVersion,
        [in] ULONG cbMetadataBlob,
        [in, size_is(cbMetadataBlob)] LPCBYTE metadataBlob,
        [in] ULONG cbEventData,
        [in, size_is(cbEventData)] LPCBYTE eventData,
        [in] LPCGUID pActivityId,
        [in] LPCGUID pRelatedActivityId,
        [in] ThreadID eventThread,
        [in] ULONG numStackFrames,
        [in, length_is(numStackFrames)] UINT_PTR stackFrames[]); 
```  
  
## <a name="parameters"></a><span data-ttu-id="b1969-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1969-106">Parameters</span></span>

<span data-ttu-id="b1969-107">`provider` 'ndaki Bu olayın kaynaklandığı sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="b1969-107">`provider` [in] The provider that this event originated from.</span></span>

<span data-ttu-id="b1969-108">`eventId` 'ndaki Teslim edilen olayın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b1969-108">`eventId` [in] The ID of the event being delivered.</span></span>

<span data-ttu-id="b1969-109">`eventVersion` 'ndaki Teslim edilen etkinliğin sürümü.</span><span class="sxs-lookup"><span data-stu-id="b1969-109">`eventVersion` [in] The version of the event being delivered.</span></span>

<span data-ttu-id="b1969-110">`cbMetadataBlob` 'ndaki Bayt cinsinden uzunluğu `metadataBlob` .</span><span class="sxs-lookup"><span data-stu-id="b1969-110">`cbMetadataBlob` [in] The length, in bytes, of `metadataBlob`.</span></span>

<span data-ttu-id="b1969-111">`metadataBlob` 'ndaki Olay için meta veri blobu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b1969-111">`metadataBlob` [in] A pointer to the metadata blob for the event.</span></span>

<span data-ttu-id="b1969-112">`cbEventData` 'ndaki Bayt cinsinden uzunluğu `eventData` .</span><span class="sxs-lookup"><span data-stu-id="b1969-112">`cbEventData` [in] The length, in bytes, of `eventData`.</span></span>

<span data-ttu-id="b1969-113">`eventData` 'ndaki Olay için yük.</span><span class="sxs-lookup"><span data-stu-id="b1969-113">`eventData` [in] The payload for the event.</span></span>

<span data-ttu-id="b1969-114">`pActivityId` 'ndaki Olayın etkinlik KIMLIĞINI veya NULL değerini temsil eden GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b1969-114">`pActivityId` [in] A pointer to the GUID that represents the event's activity ID, or NULL.</span></span>

<span data-ttu-id="b1969-115">`pRelatedActivityId` 'ndaki Olayın ilgili etkinlik KIMLIĞINI veya NULL değerini temsil eden GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b1969-115">`pRelatedActivityId` [in] A pointer to the GUID that represents the event's related activity ID, or NULL.</span></span>

<span data-ttu-id="b1969-116">`eventThread` 'ndaki Olayın gerçekleştiği iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b1969-116">`eventThread` [in] The ID of the thread the event occurred on.</span></span>

<span data-ttu-id="b1969-117">`numStackFrames` 'ndaki Dizideki öğelerin sayısı `stackFrames` .</span><span class="sxs-lookup"><span data-stu-id="b1969-117">`numStackFrames` [in] The number of elements in the `stackFrames` array.</span></span>

<span data-ttu-id="b1969-118">`stackFrames` 'ndaki Etkinliğin yönetilen çağrı yığınını temsil eden kod adresleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="b1969-118">`stackFrames` [in] An array of code addresses representing the managed callstack of the event.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1969-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1969-119">Requirements</span></span>  

<span data-ttu-id="b1969-120">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b1969-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="b1969-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1969-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="b1969-122">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1969-122">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1969-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1969-123">See also</span></span>

- [<span data-ttu-id="b1969-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b1969-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b1969-125">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1969-125">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="b1969-126">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1969-126">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="b1969-127">ICorProfilerInfo12. EventPipeStartSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1969-127">ICorProfilerInfo12.EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)
