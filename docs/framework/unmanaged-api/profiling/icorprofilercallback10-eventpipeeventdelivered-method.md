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
ms.openlocfilehash: 73f3eb64671b22b1ec16b5a5b1b24115f7f65f6d
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231342"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a><span data-ttu-id="2d707-103">ICorProfilerCallback10:: Eventpipeeventteslim edildi yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d707-103">ICorProfilerCallback10::EventPipeEventDelivered Method</span></span>

<span data-ttu-id="2d707-104">Profiler 'ın Şu anda etkin oturumuna her bir EventPipe olayı teslim edildiğinde profil oluşturucuyu bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="2d707-104">Notifies the profiler whenever an EventPipe event has been delivered to the profiler's currently active session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d707-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d707-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2d707-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d707-106">Parameters</span></span>

<span data-ttu-id="2d707-107">`provider` 'ndaki Bu olayın kaynaklandığı sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="2d707-107">`provider` [in] The provider that this event originated from.</span></span>

<span data-ttu-id="2d707-108">`eventId` 'ndaki Teslim edilen olayın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2d707-108">`eventId` [in] The ID of the event being delivered.</span></span>

<span data-ttu-id="2d707-109">`eventVersion` 'ndaki Teslim edilen etkinliğin sürümü.</span><span class="sxs-lookup"><span data-stu-id="2d707-109">`eventVersion` [in] The version of the event being delivered.</span></span>

<span data-ttu-id="2d707-110">`cbMetadataBlob` 'ndaki Bayt cinsinden uzunluğu `metadataBlob` .</span><span class="sxs-lookup"><span data-stu-id="2d707-110">`cbMetadataBlob` [in] The length, in bytes, of `metadataBlob`.</span></span>

<span data-ttu-id="2d707-111">`metadataBlob` 'ndaki Olay için meta veri blobu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d707-111">`metadataBlob` [in] A pointer to the metadata blob for the event.</span></span>

<span data-ttu-id="2d707-112">`cbEventData` 'ndaki Bayt cinsinden uzunluğu `eventData` .</span><span class="sxs-lookup"><span data-stu-id="2d707-112">`cbEventData` [in] The length, in bytes, of `eventData`.</span></span>

<span data-ttu-id="2d707-113">`eventData` 'ndaki Olay için yük.</span><span class="sxs-lookup"><span data-stu-id="2d707-113">`eventData` [in] The payload for the event.</span></span>

<span data-ttu-id="2d707-114">`pActivityId` 'ndaki Olayın etkinlik KIMLIĞINI veya NULL değerini temsil eden GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d707-114">`pActivityId` [in] A pointer to the GUID that represents the event's activity ID, or NULL.</span></span>

<span data-ttu-id="2d707-115">`pRelatedActivityId` 'ndaki Olayın ilgili etkinlik KIMLIĞINI veya NULL değerini temsil eden GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d707-115">`pRelatedActivityId` [in] A pointer to the GUID that represents the event's related activity ID, or NULL.</span></span>

<span data-ttu-id="2d707-116">`eventThread` 'ndaki Olayın gerçekleştiği iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2d707-116">`eventThread` [in] The ID of the thread the event occurred on.</span></span>

<span data-ttu-id="2d707-117">`numStackFrames` 'ndaki Dizideki öğelerin sayısı `stackFrames` .</span><span class="sxs-lookup"><span data-stu-id="2d707-117">`numStackFrames` [in] The number of elements in the `stackFrames` array.</span></span>

<span data-ttu-id="2d707-118">`stackFrames` 'ndaki Etkinliğin yönetilen çağrı yığınını temsil eden kod adresleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="2d707-118">`stackFrames` [in] An array of code addresses representing the managed callstack of the event.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d707-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d707-119">Requirements</span></span>  

<span data-ttu-id="2d707-120">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="2d707-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="2d707-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2d707-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="2d707-122">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d707-122">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d707-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d707-123">See also</span></span>

- [<span data-ttu-id="2d707-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2d707-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2d707-125">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d707-125">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="2d707-126">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d707-126">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="2d707-127">ICorProfilerInfo12. EventPipeStartSession yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d707-127">ICorProfilerInfo12.EventPipeStartSession Method</span></span>](icorprofilerinfo12-eventpipestartsession-method.md)
