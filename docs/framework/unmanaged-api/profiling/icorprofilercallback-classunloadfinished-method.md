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
ms.openlocfilehash: b78d604a28ffe01000a763f7e0dd3c1630e2c186
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435916"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="86df1-102">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86df1-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="86df1-103">Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="86df1-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86df1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86df1-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86df1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86df1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="86df1-106">'ndaki Kaldırılan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86df1-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="86df1-107">'ndaki Sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="86df1-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86df1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86df1-108">Remarks</span></span>  
 <span data-ttu-id="86df1-109">Sınıfı kaldırma işleminin bazı bölümleri `ClassUnloadFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="86df1-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="86df1-110">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="86df1-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="86df1-111">Ancak, `hrStatus` başarılı bir HRESULT, yalnızca sınıfın kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="86df1-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86df1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86df1-112">Requirements</span></span>  
 <span data-ttu-id="86df1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86df1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86df1-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="86df1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86df1-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86df1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86df1-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86df1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86df1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86df1-117">See also</span></span>

- [<span data-ttu-id="86df1-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86df1-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="86df1-119">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86df1-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
