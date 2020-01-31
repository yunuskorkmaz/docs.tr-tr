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
ms.openlocfilehash: 5b465216da39e8cf207f0614519720453c384ae9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866591"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="662b0-102">ICorProfilerCallback::ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="662b0-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="662b0-103">Profil oluşturucuyu bir sınıfın yüklenmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="662b0-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="662b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="662b0-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="662b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="662b0-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="662b0-106">\[in] yüklenmekte olan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="662b0-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="662b0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="662b0-107">Remarks</span></span>  
 <span data-ttu-id="662b0-108">`classId` değeri, [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="662b0-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="662b0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="662b0-109">Requirements</span></span>  
 <span data-ttu-id="662b0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="662b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="662b0-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="662b0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="662b0-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="662b0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="662b0-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="662b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662b0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="662b0-114">See also</span></span>

- [<span data-ttu-id="662b0-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="662b0-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
