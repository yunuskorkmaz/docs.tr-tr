---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo12:: EventPipeDefineEvent yöntemi'
title: 'ICorProfilerInfo12:: EventPipeDefineEvent yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeDefineEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 845f7f26dce7aa0f4b7d895b9f04cc89e7ac7192
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805759"
---
# <a name="icorprofilerinfo12eventpipedefineevent-method"></a><span data-ttu-id="75f07-103">ICorProfilerInfo12:: EventPipeDefineEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="75f07-103">ICorProfilerInfo12::EventPipeDefineEvent Method</span></span>

<span data-ttu-id="75f07-104">Mevcut bir sağlayıcıda EventPipe olayını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="75f07-104">Defines an EventPipe event on an existing provider.</span></span> <span data-ttu-id="75f07-105">Bu sağlayıcı, diğer dinleyicilerinin alabileceği EventPipe olaylarını yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75f07-105">This provider can be used to write EventPipe events that other listeners can receive.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="75f07-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f07-106">Syntax</span></span>  
  
```cpp  
    HRESULT EventPipeDefineEvent(
                [in] EVENTPIPE_PROVIDER     provider,
                [in, string] const WCHAR   *eventName,
                [in] UINT32                 eventID,
                [in] UINT64                 keywords,
                [in] UINT32                 eventVersion,
                [in] UINT32                 level,
                [in] UINT8                  opcode,
                [in] BOOL                   needStack,
                [in] UINT32                 cParamDescs,
                [in, size_is(cParamDescs)]
                     COR_PRF_EVENTPIPE_PARAM_DESC pParamDescs[],
                [out] EVENTPIPE_EVENT      *pEvent);
```  
  
## <a name="parameters"></a><span data-ttu-id="75f07-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75f07-107">Parameters</span></span>

<span data-ttu-id="75f07-108">`provider` 'ndaki Bir olayın tanımlanacağı sağlayıcının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="75f07-108">`provider` [in] The ID of the provider to define an event on.</span></span>

<span data-ttu-id="75f07-109">`eventName` 'ndaki Olay adını içeren, null ile sonlandırılmış geniş bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="75f07-109">`eventName` [in] A pointer to a null terminated wide character string that contains the event name.</span></span>

<span data-ttu-id="75f07-110">`eventID` 'ndaki Tanımlanmakta olan olayın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="75f07-110">`eventID` [in] The ID of the event being defined.</span></span>

<span data-ttu-id="75f07-111">`keywords` 'ndaki Tanımlanmakta olan olayın anahtar sözcükleri.</span><span class="sxs-lookup"><span data-stu-id="75f07-111">`keywords` [in] The keywords of the event being defined.</span></span>

<span data-ttu-id="75f07-112">`eventVersion` 'ndaki Tanımlanmakta olan olayın sürümü.</span><span class="sxs-lookup"><span data-stu-id="75f07-112">`eventVersion` [in] The version of the event being defined.</span></span>

<span data-ttu-id="75f07-113">`level` 'ndaki Tanımlanmakta olan olayın düzeyi.</span><span class="sxs-lookup"><span data-stu-id="75f07-113">`level` [in] The level of the event being defined.</span></span>

<span data-ttu-id="75f07-114">`opcode` 'ndaki Tanımlanmakta olan olayın işlem kodu.</span><span class="sxs-lookup"><span data-stu-id="75f07-114">`opcode` [in] The opcode of the event being defined.</span></span>

<span data-ttu-id="75f07-115">`needStack` 'ndaki `BOOL` Bu olay her tetiklendiğinde yönetilen yığınların toplanıp toplanmayacağını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="75f07-115">`needStack` [in] A `BOOL` indicating whether managed stacks should be collected each time this event fires.</span></span>

<span data-ttu-id="75f07-116">`cParamDescs` 'ndaki İçindeki parametrelerin sayısı `pParamDescs` .</span><span class="sxs-lookup"><span data-stu-id="75f07-116">`cParamDescs` [in] The count of the number of parameters in `pParamDescs`.</span></span>

<span data-ttu-id="75f07-117">`pParamDescs` 'ndaki `COR_PRF_EVENTPIPE_PARAM_DESC` Tanımlanmakta olan olaya parametre türlerini tanımlayan dizi.</span><span class="sxs-lookup"><span data-stu-id="75f07-117">`pParamDescs` [in] An array of `COR_PRF_EVENTPIPE_PARAM_DESC` defining the parameter types to the event being defined.</span></span>

<span data-ttu-id="75f07-118">`pEvent` dışı Çağıran, işlev döndürdüğünde tanımlanmakta olan olayın KIMLIĞIYLE doldurulacak bir işaretçi sağladı.</span><span class="sxs-lookup"><span data-stu-id="75f07-118">`pEvent` [out] A caller provided pointer that will be filled with the ID of the event being defined when the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="75f07-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75f07-119">Requirements</span></span>  

<span data-ttu-id="75f07-120">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="75f07-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="75f07-121">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f07-121">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="75f07-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f07-122">See also</span></span>

- [<span data-ttu-id="75f07-123">EventPipe genel bakış</span><span class="sxs-lookup"><span data-stu-id="75f07-123">EventPipe Overview</span></span>](../../../core/diagnostics/eventpipe.md)
- [<span data-ttu-id="75f07-124">İyi bilinen EventProviders</span><span class="sxs-lookup"><span data-stu-id="75f07-124">Well Known EventProviders</span></span>](../../../core/diagnostics/well-known-event-providers.md)
- [<span data-ttu-id="75f07-125">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="75f07-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="75f07-126">ICorProfilerCallback10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="75f07-126">ICorProfilerCallback10 Interface</span></span>](icorprofilercallback10-interface.md)
- [<span data-ttu-id="75f07-127">ICorProfilerInfo12 arabirimi</span><span class="sxs-lookup"><span data-stu-id="75f07-127">ICorProfilerInfo12 Interface</span></span>](icorprofilerinfo12-interface.md)
- [<span data-ttu-id="75f07-128">COR_PRF_EVENTPIPE_PARAM_DESC yapısı</span><span class="sxs-lookup"><span data-stu-id="75f07-128">COR_PRF_EVENTPIPE_PARAM_DESC Structure</span></span>](cor-prf-eventpipe-param-desc-structure.md)
