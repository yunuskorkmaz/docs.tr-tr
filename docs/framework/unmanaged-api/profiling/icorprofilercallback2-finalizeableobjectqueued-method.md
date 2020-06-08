---
title: ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: e2e01c396a67614464e3d4ca50de992388961463
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499834"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="96e94-102">ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96e94-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="96e94-103">Kod Profilcisi, sonlandırıcısı olan bir nesnenin, yönteminin yürütülmesi için Sonlandırıcı iş parçacığına sıraya alınmış olduğunu bildirir `Finalize` .</span><span class="sxs-lookup"><span data-stu-id="96e94-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96e94-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="96e94-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96e94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96e94-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="96e94-106">'ndaki Sonlandırıcının yönlerini açıklayan [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="96e94-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="96e94-107">'ndaki Kuyruğa alınmış nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="96e94-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96e94-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96e94-108">Requirements</span></span>  
 <span data-ttu-id="96e94-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96e94-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96e94-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="96e94-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96e94-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96e94-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96e94-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96e94-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96e94-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96e94-113">See also</span></span>

- [<span data-ttu-id="96e94-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96e94-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="96e94-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96e94-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
