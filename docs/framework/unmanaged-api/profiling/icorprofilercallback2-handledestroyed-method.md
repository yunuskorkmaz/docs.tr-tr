---
title: ICorProfilerCallback2::HandleDestroyed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
ms.openlocfilehash: 06064d82e5f572de08e56fd83923134a94d5e77b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731936"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="611ec-102">ICorProfilerCallback2::HandleDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="611ec-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>

<span data-ttu-id="611ec-103">Kod Profilcisi bir çöp toplama tanıtıcısının yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="611ec-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611ec-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="611ec-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="611ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="611ec-105">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="611ec-106">'ndaki Çöp toplama tanıtıcısının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="611ec-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="611ec-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="611ec-107">Requirements</span></span>  

 <span data-ttu-id="611ec-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="611ec-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="611ec-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="611ec-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="611ec-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="611ec-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="611ec-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="611ec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611ec-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="611ec-112">See also</span></span>

- [<span data-ttu-id="611ec-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="611ec-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="611ec-114">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="611ec-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
