---
title: ICorProfilerCallback::ClassLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: c9faff2d616d03d823c80fb2d9cd71d5fd5759ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445087"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="2970a-102">ICorProfilerCallback::ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2970a-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="2970a-103">Profil oluşturucuyu bir sınıfın yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2970a-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2970a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2970a-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2970a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2970a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2970a-106">'ndaki Yüklenmekte olan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2970a-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2970a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2970a-107">Remarks</span></span>  
 <span data-ttu-id="2970a-108">`classId` değeri, [ICorProfilerCallback:: ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2970a-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2970a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2970a-109">Requirements</span></span>  
 <span data-ttu-id="2970a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2970a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2970a-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2970a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2970a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2970a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2970a-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2970a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2970a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2970a-114">See also</span></span>

- [<span data-ttu-id="2970a-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2970a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
