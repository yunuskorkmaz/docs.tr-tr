---
description: ': ICorProfilerCallback:: ModuleUnloadStarted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ModuleUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 3d10654e23481fe6f8956129a0aef7ed4206bba9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745235"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="686c2-103">ICorProfilerCallback::ModuleUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="686c2-103">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>

<span data-ttu-id="686c2-104">Profil oluşturucuyu bir modülün kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="686c2-104">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="686c2-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="686c2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="686c2-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="686c2-107">'ndaki Kaldırılmakta olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="686c2-107">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="686c2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="686c2-108">Remarks</span></span>  

 <span data-ttu-id="686c2-109">Değeri, `moduleId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil — bu `ModuleUnloadStarted` modülle ilgili bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="686c2-109">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="686c2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="686c2-110">Requirements</span></span>  

 <span data-ttu-id="686c2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="686c2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="686c2-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="686c2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="686c2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="686c2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="686c2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="686c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686c2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="686c2-115">See also</span></span>

- [<span data-ttu-id="686c2-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="686c2-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="686c2-117">ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="686c2-117">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
