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
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175154"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="c3544-102">ICorProfilerCallback::ModuleUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3544-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="c3544-103">Profiloluşturucuya bir modülün boşaltıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3544-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3544-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3544-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="c3544-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3544-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c3544-106">[içinde] Boşaltılan modülün kimliği.</span><span class="sxs-lookup"><span data-stu-id="c3544-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3544-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3544-107">Remarks</span></span>  
 <span data-ttu-id="c3544-108">Yöntem döndükten sonra `moduleId` `ModuleUnloadStarted` bir bilgi isteği için değeri geçerli değildir — bu, profiloluşturucunun bu modül hakkında bilgi almak için son şansıdır.</span><span class="sxs-lookup"><span data-stu-id="c3544-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3544-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3544-109">Requirements</span></span>  
 <span data-ttu-id="c3544-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3544-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3544-111">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3544-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3544-112">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3544-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3544-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3544-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3544-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3544-114">See also</span></span>

- [<span data-ttu-id="c3544-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3544-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c3544-116">ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3544-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
