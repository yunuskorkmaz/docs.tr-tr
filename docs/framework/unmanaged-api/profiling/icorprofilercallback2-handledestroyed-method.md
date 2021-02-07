---
description: 'Daha fazla bilgi edinin: ICorProfilerCallback2:: Handleyok etme yöntemi'
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
ms.openlocfilehash: d583a2170efbb4ebe72d7eacdd60af1a089a518f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705605"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="e64cc-103">ICorProfilerCallback2::HandleDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e64cc-103">ICorProfilerCallback2::HandleDestroyed Method</span></span>

<span data-ttu-id="e64cc-104">Kod Profilcisi bir çöp toplama tanıtıcısının yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="e64cc-104">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64cc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e64cc-105">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e64cc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e64cc-106">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="e64cc-107">'ndaki Çöp toplama tanıtıcısının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e64cc-107">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e64cc-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e64cc-108">Requirements</span></span>  

 <span data-ttu-id="e64cc-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e64cc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e64cc-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e64cc-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e64cc-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e64cc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e64cc-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e64cc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64cc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e64cc-113">See also</span></span>

- [<span data-ttu-id="e64cc-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e64cc-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e64cc-115">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e64cc-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
