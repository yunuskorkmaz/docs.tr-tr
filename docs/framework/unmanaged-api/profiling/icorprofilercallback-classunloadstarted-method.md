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
ms.openlocfilehash: 91de255b2214ad0c6ce6911d9533df593142a191
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760684"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="74dbc-103">ICorProfilerCallback::ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74dbc-103">ICorProfilerCallback::ClassUnloadStarted Method</span></span>

<span data-ttu-id="74dbc-104">Profil oluşturucuyu bir sınıfın kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="74dbc-104">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74dbc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74dbc-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74dbc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74dbc-106">Parameters</span></span>

<span data-ttu-id="74dbc-107">`classId` 'ndaki Kaldırılmakta olan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="74dbc-107">`classId` [in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="74dbc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74dbc-108">Remarks</span></span>  

 <span data-ttu-id="74dbc-109">Değeri, `classId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil `ClassUnloadStarted` — Bu sınıf hakkında bilgi edinmek için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="74dbc-109">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74dbc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74dbc-110">Requirements</span></span>  

 <span data-ttu-id="74dbc-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74dbc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74dbc-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74dbc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74dbc-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74dbc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74dbc-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74dbc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74dbc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74dbc-115">See also</span></span>

- [<span data-ttu-id="74dbc-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74dbc-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="74dbc-117">ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74dbc-117">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
