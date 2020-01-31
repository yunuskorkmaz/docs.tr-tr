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
ms.openlocfilehash: c09d896e59a6c336fbe4923dbe85f30b039d8c36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866409"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="c6594-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6594-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="c6594-103">Profil oluşturucuyu, özel durum işlemenin arama aşamasının geçerli özel durum için bir işleyici bulmak üzere bir işlev aramaya başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="c6594-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6594-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6594-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6594-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6594-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c6594-106">\[içinde] girilen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c6594-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="c6594-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6594-107">Requirements</span></span>  
 <span data-ttu-id="c6594-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6594-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6594-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6594-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6594-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c6594-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6594-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6594-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6594-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6594-112">See also</span></span>

- [<span data-ttu-id="c6594-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6594-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c6594-114">ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6594-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
