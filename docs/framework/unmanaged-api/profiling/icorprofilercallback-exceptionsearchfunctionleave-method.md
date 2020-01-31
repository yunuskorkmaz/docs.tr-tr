---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
ms.openlocfilehash: bbd4c9e40f257cc66b638ba01ef8e51205922ece
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866397"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="2c4db-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c4db-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="2c4db-103">Profil oluşturucuya özel durum işlemenin arama aşamasının bir işlev aramayı bitirmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c4db-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c4db-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="2c4db-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c4db-105">Requirements</span></span>  
 <span data-ttu-id="2c4db-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c4db-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c4db-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2c4db-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c4db-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c4db-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c4db-109">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c4db-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c4db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c4db-110">See also</span></span>

- [<span data-ttu-id="2c4db-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c4db-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2c4db-112">ExceptionSearchFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c4db-112">ExceptionSearchFunctionEnter Method</span></span>](icorprofilercallback-exceptionsearchfunctionenter-method.md)
