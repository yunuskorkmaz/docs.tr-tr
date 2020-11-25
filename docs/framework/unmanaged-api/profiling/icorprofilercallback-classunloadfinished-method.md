---
title: ICorProfilerCallback::ClassUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 114d5d58d0d9098944299aefd0cb99a70c5da09d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700269"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="22095-102">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22095-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="22095-103">Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="22095-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22095-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="22095-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22095-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22095-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="22095-106">\[' de], kaldırılan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22095-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="22095-107">\[içinde] sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="22095-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="22095-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22095-108">Remarks</span></span>  

 <span data-ttu-id="22095-109">Sınıfı kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `ClassUnloadFinished` .</span><span class="sxs-lookup"><span data-stu-id="22095-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="22095-110">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="22095-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="22095-111">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca sınıfın kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="22095-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22095-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22095-112">Requirements</span></span>  

 <span data-ttu-id="22095-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22095-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22095-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="22095-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22095-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="22095-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22095-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22095-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22095-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22095-117">See also</span></span>

- [<span data-ttu-id="22095-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22095-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="22095-119">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22095-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
