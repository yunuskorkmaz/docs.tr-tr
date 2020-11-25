---
title: ICorProfilerCallback::ModuleLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: 6fbd009b5785c5dc78df81e4411fbdf8e8eadf71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730343"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="543e2-102">ICorProfilerCallback::ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="543e2-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>

<span data-ttu-id="543e2-103">Profil oluşturucuyu bir modülün yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="543e2-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543e2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="543e2-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="543e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="543e2-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="543e2-106">'ndaki Yüklenmekte olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="543e2-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="543e2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="543e2-107">Remarks</span></span>  

 <span data-ttu-id="543e2-108">Değeri, `moduleId` [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="543e2-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="543e2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="543e2-109">Requirements</span></span>  

 <span data-ttu-id="543e2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="543e2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543e2-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="543e2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="543e2-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="543e2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="543e2-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543e2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="543e2-114">See also</span></span>

- [<span data-ttu-id="543e2-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="543e2-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
