---
description: ': ICorProfilerCallback:: ExceptionSearchFunctionEnter yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d9989ef8b1ae50202ba6900b95504a7d50e10dfc
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759488"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="672d3-103">ICorProfilerCallback::ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="672d3-103">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>

<span data-ttu-id="672d3-104">Profil oluşturucuyu, özel durum işlemenin arama aşamasının geçerli özel durum için bir işleyici bulmak üzere bir işlev aramaya başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="672d3-104">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="672d3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="672d3-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="672d3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="672d3-106">Parameters</span></span>

<span data-ttu-id="672d3-107">`functionId` 'ndaki Girilen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="672d3-107">`functionId` [in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="672d3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="672d3-108">Requirements</span></span>  

 <span data-ttu-id="672d3-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="672d3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="672d3-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="672d3-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="672d3-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="672d3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="672d3-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="672d3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672d3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="672d3-113">See also</span></span>

- [<span data-ttu-id="672d3-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="672d3-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="672d3-115">ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="672d3-115">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
