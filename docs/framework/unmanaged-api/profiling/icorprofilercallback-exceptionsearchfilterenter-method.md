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
ms.openlocfilehash: 710dbe70b0a2498a3d521cdc813c4ead7ba6442e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866435"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="4c8a7-102">ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c8a7-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="4c8a7-103">Profil oluşturucuyu, özel durum işlemenin arama aşamasının Kullanıcı tanımlı bir özel durum filtresi yürütmeye başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="4c8a7-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c8a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c8a7-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c8a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c8a7-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="4c8a7-106">\[içinde] filtreyi içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4c8a7-106">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c8a7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c8a7-107">Requirements</span></span>  
 <span data-ttu-id="4c8a7-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c8a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c8a7-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4c8a7-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c8a7-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4c8a7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c8a7-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c8a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8a7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c8a7-112">See also</span></span>

- [<span data-ttu-id="4c8a7-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c8a7-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4c8a7-114">ExceptionSearchFilterLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c8a7-114">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
