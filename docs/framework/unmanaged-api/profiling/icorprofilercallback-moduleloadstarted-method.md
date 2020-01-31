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
ms.openlocfilehash: 88da5a968bf224dc5b6f45ee5d1d2e75386086f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866162"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="27f6e-102">ICorProfilerCallback::ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27f6e-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="27f6e-103">Profil oluşturucuyu bir modülün yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="27f6e-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27f6e-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27f6e-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="27f6e-106">'ndaki Yüklenmekte olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="27f6e-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27f6e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27f6e-107">Remarks</span></span>  
 <span data-ttu-id="27f6e-108">[ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) yöntemi çağrılana kadar `moduleId` değeri bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="27f6e-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f6e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27f6e-109">Requirements</span></span>  
 <span data-ttu-id="27f6e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f6e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f6e-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="27f6e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27f6e-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="27f6e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27f6e-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f6e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f6e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27f6e-114">See also</span></span>

- [<span data-ttu-id="27f6e-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27f6e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
