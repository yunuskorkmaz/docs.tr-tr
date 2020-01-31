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
ms.openlocfilehash: 5d9474f78dd8b999a37f60e0698cfd04240b897a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866578"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="2e8ff-102">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e8ff-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="2e8ff-103">Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e8ff-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e8ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e8ff-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="2e8ff-106">\[in], bellekten kaldırılan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="2e8ff-107">\[, sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="2e8ff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e8ff-108">Remarks</span></span>  
 <span data-ttu-id="2e8ff-109">Sınıfı kaldırma işleminin bazı bölümleri `ClassUnloadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="2e8ff-110">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2e8ff-111">Ancak, `hrStatus` başarılı bir HRESULT, yalnızca sınıfın kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e8ff-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e8ff-112">Requirements</span></span>  
 <span data-ttu-id="2e8ff-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e8ff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e8ff-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2e8ff-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e8ff-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e8ff-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e8ff-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e8ff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8ff-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e8ff-117">See also</span></span>

- [<span data-ttu-id="2e8ff-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e8ff-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2e8ff-119">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e8ff-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
