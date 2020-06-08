---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: 244227aadb50720514f7511be563089d520b4bf5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500201"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="9ec4b-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec4b-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="9ec4b-103">Profil oluşturucuyu, özel durum işlemenin arama aşamasının geçerli özel durum için bir işleyici bulmak üzere bir işlev aramaya başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="9ec4b-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec4b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9ec4b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ec4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ec4b-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9ec4b-106">\[' de] girilen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9ec4b-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9ec4b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ec4b-107">Requirements</span></span>  
 <span data-ttu-id="9ec4b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec4b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec4b-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ec4b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ec4b-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9ec4b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec4b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec4b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec4b-112">See also</span></span>

- [<span data-ttu-id="9ec4b-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ec4b-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9ec4b-114">ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ec4b-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
