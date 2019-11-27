---
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
ms.openlocfilehash: f0000e9b063022e828e52b9b940ec6f4e0ce4165
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445897"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="1b064-102">ICorProfilerCallback::ModuleUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b064-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="1b064-103">Profil oluşturucuyu bir modülün kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b064-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b064-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b064-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="1b064-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b064-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1b064-106">'ndaki Kaldırılmakta olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1b064-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b064-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b064-107">Remarks</span></span>  
 <span data-ttu-id="1b064-108">`moduleId` değeri `ModuleUnloadStarted` yöntemi çağrıldıktan sonra bir bilgi isteği için geçerli değil — bu modülle ilgili bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="1b064-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b064-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b064-109">Requirements</span></span>  
 <span data-ttu-id="1b064-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b064-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b064-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1b064-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b064-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1b064-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b064-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b064-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b064-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b064-114">See also</span></span>

- [<span data-ttu-id="1b064-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b064-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1b064-116">ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b064-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
