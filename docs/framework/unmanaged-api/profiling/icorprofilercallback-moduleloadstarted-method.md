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
ms.openlocfilehash: a04f72fff9a88c8689821131b08b35500c23b3d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503360"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="de1b7-102">ICorProfilerCallback::ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de1b7-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="de1b7-103">Profil oluşturucuyu bir modülün yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="de1b7-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1b7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="de1b7-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de1b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de1b7-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="de1b7-106">'ndaki Yüklenmekte olan modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="de1b7-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de1b7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de1b7-107">Remarks</span></span>  
 <span data-ttu-id="de1b7-108">Değeri, `moduleId` [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="de1b7-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de1b7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de1b7-109">Requirements</span></span>  
 <span data-ttu-id="de1b7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de1b7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de1b7-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="de1b7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de1b7-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="de1b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de1b7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de1b7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1b7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de1b7-114">See also</span></span>

- [<span data-ttu-id="de1b7-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de1b7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
