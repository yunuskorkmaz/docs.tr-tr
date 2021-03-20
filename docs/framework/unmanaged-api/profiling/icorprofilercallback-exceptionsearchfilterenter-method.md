---
description: ': ICorProfilerCallback:: ExceptionSearchFilterEnter Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 29a9eed75e5d8a954dfb23dedf3d2080e0d139d2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760227"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="3ef0f-103">ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ef0f-103">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>

<span data-ttu-id="3ef0f-104">Profil oluşturucuyu, özel durum işlemenin arama aşamasının Kullanıcı tanımlı bir özel durum filtresi yürütmeye başladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="3ef0f-104">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef0f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ef0f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ef0f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ef0f-106">Parameters</span></span>

<span data-ttu-id="3ef0f-107">`functionId` 'ndaki Filtreyi içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3ef0f-107">`functionId` [in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ef0f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ef0f-108">Requirements</span></span>  

 <span data-ttu-id="3ef0f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ef0f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ef0f-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3ef0f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ef0f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3ef0f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ef0f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ef0f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef0f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ef0f-113">See also</span></span>

- [<span data-ttu-id="3ef0f-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ef0f-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3ef0f-115">ExceptionSearchFilterLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ef0f-115">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
