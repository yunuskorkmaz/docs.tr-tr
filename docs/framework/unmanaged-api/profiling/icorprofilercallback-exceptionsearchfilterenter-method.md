---
title: ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: 304b8da670786851a70e38e6623d44b1bde71a04
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500240"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="210c6-102">ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="210c6-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="210c6-103">Profil oluşturucuyu, özel durum işlemenin arama aşamasının Kullanıcı tanımlı bir özel durum filtresi yürütmeye başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="210c6-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="210c6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="210c6-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="210c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="210c6-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="210c6-106">\[içinde] filtreyi içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="210c6-106">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="210c6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="210c6-107">Requirements</span></span>  
 <span data-ttu-id="210c6-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="210c6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="210c6-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="210c6-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="210c6-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="210c6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="210c6-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="210c6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="210c6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="210c6-112">See also</span></span>

- [<span data-ttu-id="210c6-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="210c6-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="210c6-114">ExceptionSearchFilterLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="210c6-114">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
