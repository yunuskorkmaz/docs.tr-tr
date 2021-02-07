---
description: ': ICorProfilerCallback:: ModuleLoadStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e8d15bece7baf82f69162663da00d331c7904837
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745274"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="2507d-103">ICorProfilerCallback::ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2507d-103">ICorProfilerCallback::ModuleLoadStarted Method</span></span>

<span data-ttu-id="2507d-104">Profil oluşturucuyu bir modülün yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2507d-104">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2507d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2507d-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2507d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2507d-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="2507d-107">'ndaki Yüklenmekte olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2507d-107">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2507d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2507d-108">Remarks</span></span>  

 <span data-ttu-id="2507d-109">Değeri, `moduleId` [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2507d-109">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2507d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2507d-110">Requirements</span></span>  

 <span data-ttu-id="2507d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2507d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2507d-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2507d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2507d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2507d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2507d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2507d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2507d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2507d-115">See also</span></span>

- [<span data-ttu-id="2507d-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2507d-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
