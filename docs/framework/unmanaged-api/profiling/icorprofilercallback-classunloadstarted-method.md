---
description: ': ICorProfilerCallback:: ClassUnloadStarted yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ClassUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 3dae88d9cbe9ed2a2e234d02420a65c6a9ca003d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706379"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="19c6e-103">ICorProfilerCallback::ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19c6e-103">ICorProfilerCallback::ClassUnloadStarted Method</span></span>

<span data-ttu-id="19c6e-104">Profil oluşturucuyu bir sınıfın kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="19c6e-104">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19c6e-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19c6e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19c6e-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="19c6e-107">\[' de], kaldırılmakta olan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="19c6e-107">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="19c6e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19c6e-108">Remarks</span></span>  

 <span data-ttu-id="19c6e-109">Değeri, `classId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil `ClassUnloadStarted` — Bu sınıf hakkında bilgi edinmek için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="19c6e-109">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19c6e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19c6e-110">Requirements</span></span>  

 <span data-ttu-id="19c6e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19c6e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19c6e-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="19c6e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19c6e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19c6e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19c6e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19c6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c6e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19c6e-115">See also</span></span>

- [<span data-ttu-id="19c6e-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19c6e-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="19c6e-117">ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19c6e-117">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
