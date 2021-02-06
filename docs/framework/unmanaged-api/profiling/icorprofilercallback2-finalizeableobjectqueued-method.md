---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback2:: Finalizeableobjectkuyruklanmış yöntemi'
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
ms.openlocfilehash: 62424ea60f72cee2328a143e4e50acd7af33e221
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647927"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="cc6c4-103">ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc6c4-103">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>

<span data-ttu-id="cc6c4-104">Kod Profilcisi, sonlandırıcısı olan bir nesnenin, yönteminin yürütülmesi için Sonlandırıcı iş parçacığına sıraya alınmış olduğunu bildirir `Finalize` .</span><span class="sxs-lookup"><span data-stu-id="cc6c4-104">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc6c4-105">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc6c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc6c4-106">Parameters</span></span>  

 `finalizerFlags`  
 <span data-ttu-id="cc6c4-107">'ndaki Sonlandırıcının yönlerini açıklayan [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="cc6c4-107">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="cc6c4-108">'ndaki Kuyruğa alınmış nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="cc6c4-108">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6c4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc6c4-109">Requirements</span></span>  

 <span data-ttu-id="cc6c4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6c4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6c4-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cc6c4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc6c4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cc6c4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc6c4-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6c4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc6c4-114">See also</span></span>

- [<span data-ttu-id="cc6c4-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc6c4-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cc6c4-116">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc6c4-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
